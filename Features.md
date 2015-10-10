# AForge.NET 1.5.1 Release #

![http://aforge.googlecode.com/svn/wiki/images/counting_detector.jpg](http://aforge.googlecode.com/svn/wiki/images/counting_detector.jpg)

This release introduces counting motion detector, which allows to count moving objects and retrieve their position and dimension. The motion detector supports motion detection as in entire video frame, as in specified zones only.

Since counting motion detector is based on blobs counting, this release also introduces number of improvements to Blob Counting algorithm, which allow blob filtering by size. Connected Components filtering was updated to use this feature and Blobs Filtering class was introduced as well, which allows to filter blobs out of specified size range.

![http://aforge.googlecode.com/svn/wiki/images/blobs_filtering.jpg](http://aforge.googlecode.com/svn/wiki/images/blobs_filtering.jpg)

[AForge.NET 1.5.1 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.5.1/Release%20notes.txt)



# AForge.NET 1.5.0 Release #

![http://aforge.googlecode.com/svn/wiki/images/partial.jpg](http://aforge.googlecode.com/svn/wiki/images/partial.jpg)

This release contains mostly improvements of AForge.Imaging library. The most improvements were caused by introduction of new base classes, which allow in-place filtering for those filters, which can not do direct manipulations on the image, and allow to do partial filtering on the specified rectangle only. Also number of registered issues were fixed in the library.

[AForge.NET 1.5.0 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.5.0/Release%20notes.txt)



# AForge.NET 1.4.2 Release #

![http://aforge.googlecode.com/svn/wiki/images/webcam.jpg](http://aforge.googlecode.com/svn/wiki/images/webcam.jpg)

This release introduces new namespace **AForge.Video.DirectShow**, which contains classes to access local video capture device (USB web cameras, for example) and video files using **DirectShow**. Motion Detection sample application was updated to demonstrate the work of new classes.

[AForge.NET 1.4.2 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.4.2/Release%20notes.txt)



# AForge.NET 1.4.1 Release #

This release introduces new features to **AForge.Imaging** namespace and different fixes to other namespaces as well.

[AForge.NET 1.4.1 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.4.1/Release%20notes.txt)

**Hough lines detector**

![http://aforge.googlecode.com/svn/wiki/images/hough_lines.gif](http://aforge.googlecode.com/svn/wiki/images/hough_lines.gif)

**Hough circles detector**

![http://aforge.googlecode.com/svn/wiki/images/hough_circles.gif](http://aforge.googlecode.com/svn/wiki/images/hough_circles.gif)



# AForge.NET 1.3.0 Release #

This release of AForge.NET adds several new namespaces to the framework:
  * AForge.Machine Learning - different algorithms of machine learning;
  * AForge.Vision - classes related to computer vision area;
  * AForge.Video - base interfaces and classes for different video processing routines;
  * AForge.Video.VFW - classes which provides access to Video for Windows API.

[AForge.NET 1.3.0 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.3.0/Release%20notes.txt)

To demonstrates new features of the release new sample applications were added.

**Motion Detector**

![http://aforge.googlecode.com/svn/wiki/images/motion_detector.jpg](http://aforge.googlecode.com/svn/wiki/images/motion_detector.jpg)

The application demonstrates the use of motion detection algorithms presented in AForge.Vision namespace and the use of video source classes. It allows playing video files and accessing JPEG and MJPEG video sources. For each video source it is possible to enable motion detection and highlight motion regions.

**Animat**

![http://aforge.googlecode.com/svn/wiki/images/animat.jpg](http://aforge.googlecode.com/svn/wiki/images/animat.jpg)

The application allows to experiment with such machine learning algorithms like QLearning and Sarsa. After agent's learning is done it is possible to view his behavior in the opened world.