# GIMP Python Object

- [gimpfuの読込](#gimpfuの読込)

- [スクリプトの終了](#gimpスクリプトの終了)

- [画像オブジェクト](#画像)

- [レイヤーオブジェクト](#レイヤー)

- [チャンネルオブジェクト](#チャンネル)

- [描画可能オブジェクト](#描画可能)


## gimpfuの読込
```python
from gimpfu import *
```

## GIMPスクリプトの終了
```python
gimp.quit()
```

## プラグインの作成
```python
#!/usr/bin/python

from gimpfu import *
#gimp.*  pdb.*  等が読み込まれる

def plugin_main():
    # ここにプラグイン実行時の処理を書く
    pass

register(
    proc_name = "プラグインの名前",
    blurb     = "プラグインに関する簡単な情報",
    help      = "プラグインの詳細情報",
    author    = "プラグインの著者",
    copyright = "プラグインの著者",
    date      = "作成日付",
    label     = "メニューに表示するプラグインの名前"
    imagetypes= "画像タイプ",
    params    = [],           #引数
    results   = [],           #戻り値
    function  = plugin_name,  #関数の名前
    menu      = "プラグインのメニューの場所"
)

main()

```

## 画像
開いた画像を表すオブジェクト
指定された寸法とタイプを作成(type = RGB or GRAY or INDEXED)
```python
# 画像を作成
img = gimp.Image(Width, Height, Color_type)

# Property----------------------------------------

# 画像のファイル名 or None
img.filename

# 画像の幅
img.width

# 画像の高さ
img.height

# フローティング選択レイヤー or None
img.floating_selection

# 画像のレイヤーリスト
img.layers

# 画像のチャンネルリスト
img.channels

# 画像の選択マスク
img.selection

# アクティブなチャンネル
img.active_channel

# アクティブなレイヤー
img.active_layer

# 画像のタイプ
img.base_type

# Method ----------------------------------------

# 画像を(width, height)にリサイズし、元の画像を(x, y)に配置する
img.resize(width, height, x, y)

# チャンネルの追加
img.add_channel(Channel, position)

# チャンネルの削除
img.remove_channnel(Channel)

# チャンネルを上げる
img.raise_channel(Channel)

# チャンネルを下げる
img.lower_channel(Channel)

# レイヤーの追加
img.add_layer(Layer, position)

# レイヤーの削除
img.remove_layer(Layer)

# レイヤーを上げる
img.raise_layer(Layer)

# レイヤーを下げる
img.lower_layer(Layer)

# レイヤーマスクの追加
img.add_layer_mask(Layer, Mask)

# 指定されたモード(APPLY or DISCARD)でレイヤーからマスクを削除
img.remove_layer_mask(Layer, mode)

# 指定されたマージタイプを使用して、画像の可視レイヤーをマージする
img.merge_visible_layers(MergeType)

# ポイント(x, y)に表示されているレイヤー、またはレイヤーが一致していない場合はNone
img.pick_correlate_layer(x, y)

# 画像のフラグを解除
img.clean_all()

# 画像の取り消しを無効にする
img.disable_undo()

# 画像の取り消しを有効にする。元に戻す
img.enable_undo()

# 可視レイヤーをマージして、非可視レイヤーを削除
img.flatten()

# コンポーネントがアクティブであればTrue
# コンポーネント = *_CHANNEL定数
img.get_components_active(component)

# コンポーネントが表示されていればTrue
img.get_component_visible(component)

# コンポーネントのアクティブ性を設定する
img.set_component_active(component, active)

# コンポーネントの可視性を設定する
img.set_component_visible(component, visible)

```
## レイヤー
画像のレイヤーを表すオブジェクト（汎用レイヤー）
```python
# レイヤー作成
layer = gimp.Layer(Image, Name, Width, Height, Type, Alpha, Mode)

# Property----------------------------------------

# 適用マスクの設定
layer.apply_mask

# ピクセル当たりのバイト数
layer.bpp

# マスクの編集設定
layer.edit_mask

# レイヤーの高さ
layer.height

# レイヤーの幅
layer.width

# レイヤーが一部である画像、またはレイヤーが添付されていない場合はNone
layer.image

# このレイヤーが画像のフローティング選択かどうか
layer.is_floating_selection

# レイヤーのマスク、存在しない場合はNone
layer.mask

# レイヤーのモード
layer.mode

# レイヤーの名前
layer.name

# レイヤーの不透明度
layer.opacity

# レイヤーの保持透明度設定
layer.preserve_transparency

# Method ----------------------------------------

# レイヤーにアルファコンポーネントを追加する
layer.add_alpha()

# オプションでアルファレイヤーを使用して、レイヤーのコピーを作成
layer.copy([alpha])

# 指定した型のレイヤーマスクを作成する
layer.create_mask(type)

# レイヤーを(width, height)にリサイズし、元のレイヤーを(x, y)に配置する
layer.resize(width, height, x, y)

# 指定された原点(origin)を使用してレイヤーを(width, height)にスケーリングする
layer.scale(height, width, origin)

# 画像の原点を基準にしてレイヤーのオフセットを設定する
layer.set_offset(x, y)

# レイヤーを現在の位置に対して(x, y)に移動する
layer.translate(x, y)

```

## チャンネル
画像のカラーチャンネルを表すオブジェクト
Colorは *_CHANNEL定数
```python
# チャンネルを作成
channel = gimp.Channel(Image, Name, Width, Height, Alpha, Color)

# Property----------------------------------------

# チャンネルの色
channel.colour
channel.color

# チャンネルの高さ
channel.height

# チャンネルの幅
channel.width

# チャンネルが属する画像、属していなければNone
channel.image

# チャンネルのレイヤー、存在しなければNone
channel.layer

# チャンネルのレイヤーマスク、存在しなければNone
channel.layer_mask

# チャンネルの名前
channel.name

# チャンネルの不透明度
channel.opacity

# チャンネルのマスク値
channel.show_masked

# チャンネルが表示されているかどうか
channel.visible

# Method ----------------------------------------

# チャンネルをコピーする
channel.copy()

```

## 描画可能
レイヤーとチャンネルの両方が描画可能オブジェクト
両方のオブジェクトにたいして実行できる操作もしくは共通の属性と方法がある

```python
# Property----------------------------------------
# ピクセルあたりのバイト数
Drawable.bpp

# 描画可能オブジェクトが色かどうか
Drawable.is_colour
Drawable.is_color
Drawable.is_rgb

# 描画可能オブジェクトがグレースケールかどうか
Drawable.is_gray
Drawable.is_grey

# 描画可能オブジェクトにアルファチャンネルがあるかどうか
Drawable.has_alpha

# 描画可能オブジェクトの高さ
Drawable.height

# 描画可能オブジェクトの幅
Drawable.width

# 描画可能オブジェクトが属する画像オブジェクト
Drawable.image

# 描画可能オブジェクトがインデックス付きカラースキームを私用するかどうか
Drawable.is_indexed

# 描画可能オブジェクトの選択の境界
Drawable.mask_bounds

# 描画可能オブジェクトの名前
Drawable.name

# 描画可能オブジェクトの左上隅のオフセット
Drawable.offsets

# 描画可能オブジェクトのタイプ
Drwaable.type

# 描画可能オブジェクトが表示されているかどうか
Drawable.visible

# Method ----------------------------------------

# 指定されたfill_type(*_FILL定数)で描画可能オブジェクトを塗りつぶす
Drawable.fill(fill_type)



```

