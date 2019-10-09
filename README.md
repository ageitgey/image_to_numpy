# image_to_numpy

Load an image file into a numpy array - while automatically rotating the image based on 
Exif orientation. Prevents upside-down and sideways images! 

![](https://user-images.githubusercontent.com/896692/66508645-6d9f6700-eac9-11e9-8e3c-51c1fcb92b87.png)

```
import image_to_numpy

img = image_to_numpy.load_image_file("my_file.jpg")
```

The image is automatically rotated into the correct orientation if the image contains Exif orientation metadata.
Otherwise, it is loaded normally.

From there, you can pass the numpy array to any Python library that works with images
in numpy array format, like face_recognition, Keras, etc.

## Installation

You can install from [PyPI](https://pypi.org/project/image_to_numpy/):

    pip install image_to_numpy

## Usage

 ```python
import image_to_numpy

img = image_to_numpy.load_image_file("my_file.jpg")
```

Your image is loaded - with the correct orientation! 

By default, the image array is returned as a numpy array 
with 3-channels of 8-bit RGB data.

You can control the output format by passing in an optional `mode` parameter:

 ```python
import image_to_numpy

img = image_to_numpy.load_image_file("my_file.jpg", mode="RGB")

# Supported modes:
#  1 (1-bit pixels, black and white, stored with one pixel per byte)
#  L (8-bit pixels, black and white)
#  RGB (3x8-bit pixels, true color)
#  RGBA (4x8-bit pixels, true color with transparency mask)
#  CMYK (4x8-bit pixels, color separation)
#  YCbCr (3x8-bit pixels, color video format)
#  I (32-bit signed integer pixels)
#  F (32-bit floating point pixels)
```


If you have matplotlib installed, here's a quick way to show your image
on the screen:

```python
import matplotlib.pyplot as plt
import image_to_numpy

img = image_to_numpy.load_image_file("my_file.jpg")

plt.imshow(img)
plt.show()
```

## Thanks

- EXIF test images used in the unittests created by Dave Perrett / @daveperrett
  - https://github.com/recurser/exif-orientation-examples
