---
layout: default
title: Images
nav_order: 13
---

# Overview of Working with Images

By leveraging the power of some common libraries that you can install, such as PILLOW, Python gains the ability to work with and manipulate images for simple tasks. You can install Pillow by running:

    pip install pillow
    
In case of any issues, you can refer to their [official documentation](http://pillow.readthedocs.io/en/3.4.x/installation.html) on installation. But for most computers, the simple pip install method should work.

---
____
**Note: When working with images in the jupyter notebook, you may get the following warning:**

    IOPub data rate exceeded.
    The notebook server will temporarily stop sending output
    to the client in order to avoid crashing it.
    To change this limit, set the config variable
    `--NotebookApp.iopub_data_rate_limit`.
    
**If you get this warning, try stopping the notebook at the command line, then restarting it with:**

    jupyter notebook --NotebookApp.iopub_data_rate_limit=1.0e10
    
** At the command line. Basically this adds a "flag" that the limit should be raised during this session of jupyter notebook that you are running.**


----


# Working with Pillow Library

## Opening Images

You can use Pillow to open image files. For a jupyter notebook, to show the file simply type the variable name holding the image. For other IDEs , the image variable will have a [.show() method.](https://stackoverflow.com/questions/28139637/how-can-i-display-an-image-using-pillow)


```python
from PIL import Image
```


```python
mac = Image.open('example.jpg')
```


```python
# Note this is a specialized file type from PIL (pillow)
type(mac)
```




    PIL.JpegImagePlugin.JpegImageFile




```python
# Only for jupyter notebook , use mac.show() for other IDEs 
mac
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_6_0.png)
    



### Image Information


```python
# (width, height)
mac.size
```




    (1993, 1257)




```python
mac.filename
```




    'example.jpg'




```python
mac.format_description
```




    'JPEG (ISO 10918)'



## Cropping Images

To crop images (that is grab a sub section) you can use the crop() method on the image object. The crop() method returns a rectangular region from this image. The box is a 4-tuple defining the left, upper, right, and lower pixel coordinate.

Note! If you take a look at the documentation string, it says the tuple you pass in is defined as (x,y,w,h). These variables can be a bit decieving. Its not really a height or width that is being passed, but instead the end coordinates of your width and height.


All the coordinates of box (x, y, w, h) are measured from the top left corner of the image. Again, all 4 of these values are coordinates!


```python
mac.crop((0,0,100,100))
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_12_0.png)
    



For the mac image this isn't a very useful demonstration. Let's use another image instead:


```python
pencils = Image.open("pencils.jpg")
```


```python
pencils
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_15_0.png)
    



Now let's attempt to grab some of the top pencils from the corner


```python
pencils.size
```




    (1950, 1300)




```python
# Start at top corner (0,0)
x = 0
y = 0

# Grab about 10% in y direction , and about 30% in x direction
w = 1950/3
h = 1300/10

pencils.crop((x,y,w,h))
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_18_0.png)
    




```python
pencils
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_19_0.png)
    



Now let's try the pencils from the bottom


```python
pencils.size
```




    (1950, 1300)




```python
x = 0 
y = 1100
w = 1950/3
h = 1300
```


```python
pencils.crop((x,y,w,h))
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_23_0.png)
    



Now let's go back to the mac photo and see if we can only grab the computer itself:


```python
mac
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_25_0.png)
    




```python
mac.size
```




    (1993, 1257)




```python
halfway = 1993/2
```


```python
x = halfway - 200
w = halfway + 200
```


```python
y = 800
h = 1257
```


```python
mac.crop((x,y,w,h))
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_30_0.png)
    



### Copying and Pasting Images

We can create copies with the copy() method and paste images on top of others with the paste() method.


```python
computer = mac.crop((x,y,w,h))
```


```python
mac.paste(im=computer,box=(0,0))
```


```python
mac
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_34_0.png)
    




```python
mac.paste(im=computer,box=(796,0))
```


```python
mac
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_36_0.png)
    



### Resizing

You can use the resize() method to resize an image


```python
mac.size
```




    (1993, 1257)




```python
h,w = mac.size
```


```python
new_h = int(h/3)
new_w = int(w/3)
```


```python
# Note this is not permanent change
# for permanent change, do a reassignment
# e.g. mac = mac.resize((100,100))
mac.resize((new_h,new_w))
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_41_0.png)
    



Can also stretch and squeeze


```python
mac.resize((3000,500))
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_43_0.png)
    



### Rotating Images

You can rotate images by specifying the amount of degrees to rotate on the rotate() method. The original dimensions will be kept and "filled" in with black. You can optionally pass in the expand parameter to fill the new rotated image to the old dimensions.


```python
pencils.rotate(90)
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_45_0.png)
    




```python
pencils.rotate(90,expand=True)
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_46_0.png)
    



Notice what happens when we rotate by 120.


```python
# The image is cut off
pencils.rotate(120)
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_48_0.png)
    




```python
#pencils.rotate(120,expand=True)
```

## Transparency  

We can add an alpha value (RGBA stands for RED,Green,Blue, Alpha) where values can go from 0 to 255. If Alpha is 0 the image is completely transparent, if it is 255 then its completely opaque.

You can create your own color here to check for possible values: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Colors/Color_picker_tool

We can adjust image alpha values with the putalpha() method:


```python
red = Image.open('red_color.jpg')
```


```python
red
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_52_0.png)
    




```python
blue = Image.open('blue_color.png')
```


```python
blue
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_54_0.png)
    




```python
red.putalpha(128)
```


```python
red
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_56_0.png)
    




```python
blue.putalpha(128)
```


```python
blue
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_58_0.png)
    




```python
blue.paste(red,box=(0,0),mask=red)
```


```python
# Get back an image that is more purple.
blue
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_60_0.png)
    



Transparency and masking can be much more complex than what we've shown here, if you find yourself needing something more, check out the documentation: https://pillow.readthedocs.io/en/stable/

## Saving Images

Let's save this updated "blue" image as 'purple.png' in this folder.


```python
blue.save("purple.png")
```

Let's check to make sure that worked:


```python
purple = Image.open("purple.png")
```


```python
purple
```




    
![png](00-Overview-of-Working-with-Images_files/00-Overview-of-Working-with-Images_67_0.png)
    



Great job!
