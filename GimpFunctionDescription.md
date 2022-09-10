# GIMPのpython-fu -- HOWTO


[gimpfuの読込](#gimpfuの読込)
[スクリプトの終了](#gimpスクリプトの終了)
[プラグインの作成](#プラグインの作成)
[画像オブジェクト](#画像)


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

# チャンネルの追加
img.add_channel(Channel, position)

# レイヤーの追加
img.add_layer(Layer, position)

# レイヤーマスクの追加
img.add_layer_mask(Layer, Mask)

# 画像のフラグを解除
img.clean_all()

# 画像の取り消しを無効にする
img.disable_undo()

# 画像の取り消しを有効にする。元に戻す
img.enable_undo()







```
## レイヤー
新しいレイヤーを作成して画像へ追加
```python
# レイヤー作成
layer = gimp.Layer(Image, Name, Width, Height, Type, Alpha, Mode)

# レイヤーを画像に追加
Image.add_layer(layer, position)
```

## チャンネル
新しいチャンネルを作成して画像へ追加
Colorは *_CHANNEL定数
```python
# チャンネルを作成
channel = gimp.Channel(Image, Name, Width, Height, Alpha, Color)

# 画像にチャンネルを追加
Image.add_channel(channel, position)
```

## 表示ウィンドウを作成する
指定された画像の新しい表示ウィンドウを作成
```python
# 画像をウィンドウに表示
gimp.Display(Image)
```

## カラーパレットの操作
```python
#RGB形式の現在の背景色を含む3タプル
gimp.get_background()

#RGB形式の現在の前景色を含む3タプル
gimp.get_foreground()

#背景色を設定
gimp.set_background(Red, Green, Blue)

#前景色を設定
gimp.set_foreground(Red, Green, Blue)
```

## プログレスバー
```python
# プログレスバーを初期化
gimp.progress_init(Label)

# プログレスバーを更新する。Percent = 0.00～1.00
gimp.progress_update(Percent)
```