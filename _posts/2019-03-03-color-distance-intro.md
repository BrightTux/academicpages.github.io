While human beings are able to easily differentiate basic colors such as red, green, blue, and etc., this gets harder when the colors are mixed up. You have probably seen the following picture on the internet:

![Males vs Female - colours](https://steemitimages.com/p/hgjbkodzNPcRWemmiXzLcZH8ivvvFQUKeLTKBkbsPV1ZABfEKsXxsEmaZY4gYLpYEQdQLaC4bwnxwneA3Kpxv7PYbg?format=match&mode=fit&width=640)

Inspired by the work of https://blog.xkcd.com/2010/05/03/color-survey-results/, the aim of this project is to create a metric system which allows users to empirically determine which color it is based on the 11 basic colors as proposed by Berlin and Kay.

The 11 basic colors described were:
Black, White, Gray, Red,Green, Blue, Yellow, Orange, Pink, Purple, Brown

This work helps both humans and computers to empirically measure the distance between a "query" color and the estimated difference. This color distance measure is important as humans and computers view colors in a very different manner as visualized below:

![computer vs human](https://steemitimages.com/p/HNWT6DgoBc183GTxCi278Mq525MBLtPpou6mSbCGA84PYydpzWrqHyALdhtMqrr4NC8aaeDs5daf6attSiyaBgDFg4XGL6Lj1jhMmEi3bCgnRXhtMASD7RQKxDt?format=match&mode=fit&width=640)


In a typically JPEG image, the color range for each channel in each pixel is from 0 to 255 where 0 is usually minimum and 255 is Maximum.

Since there are 3 channels in each typically image (Red, Green and Blue) there's too many combinations of colors which exist for the purpose of this Color Distance measurement and visualization. `(256*256*256 = 16777216 COMBINATIONS!)`

![colour palettes](https://raw.githubusercontent.com/BrightTux/ColorDistance/master/screenshot/color%20palletes.JPG)

Hence, to reduce redundancy, I've selected to use 960 different shades of colors and compare them to the "ground truth" supplied by xkcd for each of the 11 basic colors.

The 960 color shades is generated using the HSV (Hue, Saturation, Value) color space where we quantized the values of Hue to 15, and Saturation and Value to 8 values. This process greatly reduces the total number of samples to 960 samples while providing a comprehensive analysis for visualization purposes.

The measurement of each sample shade is compared using 3 different comparisons, namely RGB (low-cost estimation of Luv distance), HSV distance, as well as LAB distance. The "Average" score is also provided as a means to see how much the data varies among the 3 different distance measure functions.

Sample use case:
You may also opt to use the values/mathematical operations from the repository for your work, in my case, i used the values for my research work to identify the colors of a vehicle.

Given an image:

![Sample image](https://steemitimages.com/p/8SzwQc8j2KJb2pjdT4gmiVWAfuaxgrvPvowCsk1AXyYx8C8qEL5RSCPi4UzVErRBkxVJb6suCL6kwqqgCoTY28j8W9vb6wA8t51En8WtKG4kpC11fz6?format=match&mode=fit&width=640)

I took the dominant color, and compared it with the list of values to determine the dominant color of this vehicle.

Sample screenshot of the output:

![output](https://raw.githubusercontent.com/BrightTux/ColorDistance/master/screenshot/excelProduced.JPG)

Final output can be found here: https://github.com/BrightTux/ColorDistance/blob/master/output/colorIndexes_wTable.pdf

Technology Stack

* C++, OpenCV

Roadmap
* In the future, i plan to:
  * Allow users to submit an image, and from the image, the program will compute the closest color score.
  * Allow users to compare between the RGB, HSV, and Lab distance to see which one provides the BEST results.

