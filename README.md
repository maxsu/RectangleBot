RectangleBot
============

An Open CV rectangle detector
-------------------
***

I'd like to write a rectangle detector and extractor for an image processing task I'm coding. The goal is to register arbitrarily oriented index cards as captured by a scanner bed with a colored background. Surveying the open image processing tools out there, OpenCV or SimpleCV seems like a good choice.

The goal is to learn enough OpenCV to solve simple, highly constrained instances of the problem.



To that end, we initially frame the problem in a simplified form.


#### Problem Statement

Let I be binary image containing rectangles of the foreground color, on a solid background. The rectangles are of arbitrary position and orientation, but obey the following constraints:

1. The rectangles are completely disjoint, and their boundaries are separate.
2. No rectangles touch the image boundary.
3. *Optional*: the rectangles are of known size. 
4. *Optional*: there are exactly k rectangle, for some known k.

Let F : Image -> (R^3)^k  be a function that takes such an image I and gives a vector of the positions and angular orientations of the rectangles.

More generally, relaxing constraints 3 and 4, let G : Image -> [R^5] be a function that takes I and provides a list of the rectangles in I, consisting of their position, size, and orientation.


#### Programming Resources

[OpenCV]() is written in C, has an extensive C++ interface, as well as a Java API. There are wrappers written for python and ruby, and the Java API allows use with scala, clojure, and other JVM languages. There is support for CUDA hardware and Android.

[SimpleCV]() is a simplified python wrapper for OpenCV. It should allow rapid prototyping, and seems to be more well documented than OpenCV's python interface.
