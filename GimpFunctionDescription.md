# GIMPのpython-fuの関数

## Script-fuの読み込み
```python
from gimpfu import *
```

## 画像を作成する
指定された寸法とタイプを作成(type = RGB or GRAY or INDEXED)
```python
gimp.Image(Width, Height, Color_type)
```
## レイヤーを作成する
新しいレイヤーを作成して画像へ追加
```python
layer = gimp.Layer(Image, Name, Width, Height, Type, Alpha, Mode)

Image.add_layer(layer)
```

## チャンネルを作成する
新しいチャンネルを作成して画像へ追加
Colorは *_CHANNEL定数
```python
channel = gimp.Channel(Image, Name, Width, Height, Alpha, Color)

Image.add_channel(channel)
```

## 表示ウィンドウを作成する
指定された画像の新しい表示ウィンドウを作成
```python
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

