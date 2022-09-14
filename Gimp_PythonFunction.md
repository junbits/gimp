# GIMP Python Function

- [gimpfuの読込](#gimpfuの読込)

- [スクリプトの終了](#gimpスクリプトの終了)

- [プラグインの作成](#プラグインの作成)

- [ディスプレイに表示](#表示ウィンドウを作成する)

- [カラーパレット](#カラーパレットの操作)

- [プログレスバー](#プログレスバー)



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