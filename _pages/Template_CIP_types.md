

This page describes the type and usage of parameters in [[CIP]] package. 

=Types=

*'''Image''':any image type in: IJ1 ImagePlus, IJ2 Dataset, IJ2 ImgPlus, ImgLib2 Img, ImgLib2 RandomAccessInterval (RAI), CIP image which implements RAI and adds a thin layer of metadata (units, pixel size, axes names). output image are always a CIP image. Converters allows to get back to IJ1 or IJ2 format if needed.
*'''Region''':any type in: IJ1 Roi, ImgLib2 IterableRegion, or CIP regions which implement IterableRegion and a thin layer of metadata.
*'''Table''': a a dictionnary that maps strings to object, most likely string or scalar but possibly Region or Image too
*'''Scalar(s)''': a numeric value (or a list of numeric values) as available in script langage.
*'''String(s)''': a string of character or list of string as available in script langage
*'''Logic''': a boolean (i.e. true or false value).


=Required and Optionnal Parameters=

In CIP each function has '''required parameters that must be provided''' for the function to run. This parameters are indicated by an '''*''' in the documentation.

Each function als has some '''optionnal parameter that can be skipped''' if you don't need them. If an optionnal parameters is not provided it will be replaced by a sensible default value described in the documentation

There are different ways of skiping an optionnal parameters:
* if they are at the end of the signature you can just drop them and the function will work using defaults value for them. <br> <code>out = cip.gauss(myImage, myRadius,myBoundary)</code> or even <br> <code>out = cip.gauss(myImage, myRadius)</code>
* if they are in the middle of the signature you can either
** replace them by the null value of your scripting langage. <br> <code>cip.gauss(myImage, myRadius, None, myPixelSize)</code> where None is the null value in Jython
** drop the parameter and used named parameter for the remaining parameter you need <br> <code>cip.gauss(myImage, myRadius, 'pixelsize', myPixelSize)</code> that is maybe easier to read.


=Positional and Named Parameters=

There are 2 ways to pass the parameters to a CIP function: 
* by passing in the same position and order as the example signature provided in the documentation. If we take the gauss function as example it would write as follows using only the required parameters: <br> <code> out = gauss(in , myRadius )</code>
* by passing a string/value <br> <code>out = gauss(in , 'radius', myRadius) </code>  or even <br><code>out = gauss('radius', myRadius, 'inputImage', in )</code>