RectangleBot
============

An Open CV rectangle detector
-------------------
***

I'd like to write a rectangle detector and extractor for an image processing task I'm coding. The goal initial goal is to register arbitrarily oriented index cards as captured by a scanner bed with a colored background. Surveying the open image processing tools out there, OpenCV or SimpleCV seem like a good choices.

The goal is to learn enoug to solve simple, highly constrained instances of the problems, and then generalize to real world versions of the problem.



To that end, we initially frame the problem in a simplified form.


#### Problem Statement

Let I be binary image containing rectangles of the foreground color, on a solid background. The rectangles are of arbitrary position and orientation, but obey the following constraints:

1. The rectangles and their boundaries are completely disjoint from one another.
2. No rectangles touch the image boundary.
3. *Optional*: the rectangles are of known size. 
4. *Optional*: there are exactly k rectangle, for some known k.
5. *Advanced Topic*: Each rectangle is distorted by an arbitrary affine transform.

Let F : Image -> (R^3)^k  be a function that takes such an image I and gives a vector of the positions and angular orientations of the rectangles.

More generally, relaxing constraints 3 and 4, let G : Image -> [R^5] be a function that takes I and provides a list of the rectangles in I, consisting of their position, size, and orientation. 

As an advanced application, we will like to detect rectangles that have been transformed with an affine or perspective transform.


Conditions we will *not* cover at this time include

* Overlapping rectangles
* Low contrast backgrounds / ambiguous rectangles
* Out of focus regions / edges
* Creased / bent rectangular objects

#### Programming Resources

[OpenCV]() is written in C, has an extensive C++ interface, as well as a Java API. There are wrappers written for python and ruby, and the Java API allows use with scala, clojure, and other JVM languages. There is support for CUDA hardware and Android. Generally very fast, but difficult to use.

[SimpleCV]() is a simplified python wrapper for OpenCV. It should allow rapid prototyping, and seems to be more well documented than OpenCV's python interface. Easy to use, but slower than opencv. The authors suggest that SimpleCV can be used to quickly implement an algorithm, after which it can be easily translated to OpenCV if greater performance is needed.

#### Methods

##### Contours

Binary contour operations may be the simplest way to do this task
- Simple code
- Mostly implemented already
- Handles k rectangles
- Handles closely packed rectangles

Is not a general method
- Won't handle distorted rectangles

How it works:
1. Sharpen
2. Canny
3. Extract Contours
4. Union contours
5. Minimal Bounding Rectangles
6. Extract

##### Hough Transform

1. Sharpen
2. Canny 
3. Hough transform
4. Intersect
5. Extract

##### Rectangular Hough Transform

An efficient technique for rectangles of known size.

##### Windowed Hough Transform

An efficient and robust algorithm for tighly packed rectangles of multiple sizes.

##### Keypoint / Corner Detectors

Good at handingling general affine quadrilaterals and image stiching applications.

##### Haar Cascades

Potentially very robust algorith for advanced page detection use cases.
