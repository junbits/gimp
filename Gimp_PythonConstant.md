# GIMP Python Constant

- [ブラシ硬さの定数](#GimpBrushApplicationMode)

- [ブラシ形状の定数](#GimpBrushGeneratedShape)



## GimpBrushApplicationMode

ブラシの硬さ
```python
BRUSH_HARD = 0
BRUSH_SOFT = 1
```

## GimpBrushGeneratedShape

ブラシの形状
```python
BRUSH_GENERATED_CIRCLE = 0
BRUSH_GENERATED_SQUARE = 1
BRUSH_GENERATED_DIAMOND = 2
```

## GimpConvertDitherType

```python
NO_DITHER = 0
FS_DITHER = 1
FSLOWBLEED_DITHER = 2
FIXED_DITHER = 3
```

## GimpConvertPaletteType

```python
MAKE_PALETTE = 0
REUSE_PALETTE = 1
WEB_PALETTE = 2
MONO_PALETTE = 3
CUSTOM_PALETTE = 4
```

## GimpConvolutionType

```python
NORMAL_CONVOL = 0
ABSOLUTE_CONVOL = 1
NEGATIVE_CONVOL = 2
```

## GimpConvolveType

```python
BLUR_CONVOLVE = 0
SHARPEN_CONVOLVE = 1
```

## GimpFillType

```python
FOREGROUND_FILL = 0
BACKGROUND_FILL = 1
WHITE_FILL = 2
TRANSPARENT_FILL = 3
PATTERN_FILL = 4
```

## GimpGradientSegmentColor

```python
GRADIENT_SEGMENT_RGB = 0
GRADIENT_SEGMENT_HSV_CCW = 1
GRADIENT_SEGMENT_HSV_CW = 2
```

## GimpGradientSegmentColor

```python
GRADIENT_SEGMENT_LINEAR = 0
GRADIENT_SEGMENT_CURVED = 1
GRADIENT_SEGMENT_SINE = 2
GRADIENT_SEGMENT_SPHERE_INCREASING = 3
GRADIENT_SEGMENT_SPHERE_DECREASING = 4
```

## GimpHistogramChannel

```python
HISTGRAM_VALUE = 0
HISTGRAM_RED = 1
HISTGRAM_GREEN = 2
HISTGRAM_BLUE = 3
HISTGRAM_ALPHA = 4
```

## GimpHueRange

```python
ALL_HUES = 0
RED_HUES = 1
YELLOW_HUES = 2
GREEN_HUES = 3
CYAN_HUES = 4
BLUE_HUES = 5
MAGENTA_HUES = 6
```

## GimpInkBlobType

```python
INK_BLOB_TYPE_CIRCLE = 0
INK_BLOB_TYPE_SQUARE = 1
INK_BLOB_TYPE_DIAMOND = 2
```

## GimpLayerModeEffects

```python
NORMAL_MODE = 0
DISSOLVE_MODE = 1
BEHIND_MODE = 2
MULTIPLY_MODE = 3
SCREEN_MODE = 4
OVERLAY_MODE = 5
DIFFERENCE_MODE = 6
ADDITION_MODE = 7
SUBTRACT_MODE = 8
DARKEN_ONLY_MODE = 9
LIGHTEN_ONLY_MODE = 10
HUE_MODE = 11
SATURATION_MODE = 12
COLOR_MODE = 13
VALUE_MODE = 14
DIVIDE_MODE = 15
DODGE_MODE = 16
BURN_MODE = 17
HARDLIGHT_MODE = 18
SOFTLIGHT_MODE = 19
GRAIN_EXTRACT_MODE = 20
GRAIN_MERGE_MODE = 21
COLOR_ERASE_MODE = 22
```

## GimpMaskApplyMode

```python
MASK_APPLY = 0
MASK_DISCARD = 1
```

## GimpMergeType

```python
EXPAND_AS_NECESSARY = 0
CLIP_TO_IMAGE = 1
CLIP_TO_BOTTOM_LAYER = 2
FLATTEN_IMAGE = 3
```

## GimpOffsetType

```python
OFFSET_BACKGROUND = 0
OFFSET_TRANSPARENT = 1
```

## GimpOrientationType

```python
ORIENTATION_HORIZONTAL = 0
ORIENTATION_VERTICAL = 1
ORIENTATION_UNKNOWN = 2
```

## GimpRotationType

```python
ROTATE_90 = 0
ROTATE_180 = 1
ROTATE__270 = 2
```

## GimpSelectCriterion

```python
SELECT_CRITERION_COMPOSITE = 0
SELECT_CRITERION_R = 1
SELECT_CRITERION_G = 2
SELECT_CRITERION_B = 3
SELECT_CRITERION_H = 4
SELECT_CRITERION_S = 5
SELECT_CRITERION_V = 6
```