# AForge.NET 1.6.3 Release #

The new version of AForge.NET introduces one of the most highly requested features - changing frame rate and frame size of local capture device. Now there are DesiredFrameRate and DesiredFrameSize properties in AForge.Video.DirectShow.VideoCaptureDevice class, which allow to set desired frame rate and size (desired because it may not be provided if capture device does not support specified settings).

```
videoSource.DesiredFrameRate = 15;
videoSource.DesiredFrameSize = new Size( 320, 240 );
```

To control other properties, which may be provided by capture device/driver, it is possible to invoke capture device's property page.

```
videoSource.DisplayPropertyPage( IntPtr.Zero );
```

[AForge.NET 1.6.3 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.6.3/Release%20notes.txt)


# AForge.NET 1.6.2 Release #

This release was made because of one important issue found in Canny Edge Detector, which was causing false detection of some edge points (the filter was providing too thick edges, marking more pixels as edges than it is actually supposed). Now the issue is resolved and this edge detector produces much more accurate results.

[AForge.NET 1.6.2 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.6.2/Release%20notes.txt)


# AForge.NET 1.6.1 Release #

This release of AForge.NET introduces some very good extensions to Blob Counting. Now it is possible to specify objects' sort order returned by blob counting algorithm. Also it is possible to extract not all objects using GetObjects() method, what may be an overhead, but only "interesting" objects using partial extraction of objects with GetObjectInformation() method and then ExtractBlobsImage() method to extract image or required blob.

```
// create blob counter and process image
BlobCounter bc = new BlobCounter( sourceImage );
// specify sort order
bc.ObjectsOrder = ObjectsOrder.Size;
// get objects' information (blobs without image)
Blob[] blobs = bc.GetObjectInformation( );
// process blobs
foreach ( Blob blob in blobs )
{
    // check blob's properties
    if ( blob.Rectangle.Width > 50 )
    {
        // the blob looks interesting, let's extract it
        bc.ExtractBlobsImage( sourceImage, blob );
    }
}
```

**AForge.Imaging** library also introduces **Extract Biggest Blob** filter, which extracts the biggest blob from binary image (or from original image if it is provided).

More image processing filters:
  * [Histogram Equalization](http://en.wikipedia.org/wiki/Histogram_equalization);
  * [Contrast Stretch](http://homepages.inf.ed.ac.uk/rbf/HIPR2/stretch.htm);
  * Flat Field Correction.

**AForge.Neuro** library finally introduces neural network saving/loading functionality.

[AForge.NET 1.6.1 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.6.1/Release%20notes.txt)


# AForge.NET 1.6.0 Release #

![http://aforge.googlecode.com/svn/wiki/images/NXT-brick.jpg](http://aforge.googlecode.com/svn/wiki/images/NXT-brick.jpg)

This release introduces new namespace in AForge.NET framework - **AForge.Robotics.Lego**. For now this namespace contains classes, which allow manipulation with **Lego Mindstorms NXT** device, setting/getting its motors' state, getting information about sensors' values and retrieving generic information about the NXT brick. The namespace is supposed to grow introducing new features and it is supposed that its upper namespace (**AForge.Robotics**) eventually will include more sub namespaces with support of more Robotics stuff.

```
// create an instance of communication interface for NXT device
SerialCommunication nxtCommunication = new SerialCommunication( "COM1" );
// create an instance of NXT brick
NXTBrick nxt = new NXTBrick( nxtCommunication );
// connect to the device
if ( nxt.Connect( ) == CommunicationStatus.Success )
{
    // run motor A
    MotorState motorState = new MotorState( );

    motorState.Power      = 60;
    motorState.TurnRatio  = 50;
    motorState.Mode       = MotorMode.On;
    motorState.Regulation = RegulationMode.Idle;
    motorState.RunState   = RunState.Running;
    motorState.TachoLimit = 1000;

    nxt.SetMotorState( OutputPort.MotorA, motorState );

    // get input value from sensor 1
    InputValues inputValues;

    if ( nxt.GetInputValues( InputPort.Port1, out inputValues ) == CommunicationStatus.Success )
    {
        // ...
    }
    // ...
}
```


![http://aforge.googlecode.com/svn/wiki/images/histograms.jpg](http://aforge.googlecode.com/svn/wiki/images/histograms.jpg)

**AForge.Imaging** introduces two new classes to calculate statistics about horizontal and vertical pixels' intensities distribution, what allows detecting which parts of an image are more intensive, filled with objects or where an object has its maximum width/height. These classes may be used as in regular image analysis, as in objects' recognition based on their statistical features.

```
HorizontalIntensityStatistics his = new HorizontalIntensityStatistics( sourceImage );
VerticalIntensityStatistics   vis = new VerticalIntensityStatistics  ( sourceImage );

// process histograms ...

// to display histogram the AForge.Controls.Histogram control may be used
histogramControl.Values = his.Gray.Values;
```


![http://aforge.googlecode.com/svn/wiki/images/moravec.jpg](http://aforge.googlecode.com/svn/wiki/images/moravec.jpg)

**AForge.Imaging** introduces [Moravec corners detector](http://www.cim.mcgill.ca/~dparks/CornerDetector/mainMoravec.htm) implementing ICornersDetector interface. As the above image shows the use of its filter is limited to some certain cases, what is caused by some limitations of Moravec operator (anisotropic response, etc.). Other corners detection algorithms are going to be provided in future releases.

```
// create corner detector's instance
MoravecCornersDetector mcd = new MoravecCornersDetector( );
// process image searching for corners
Point[] corners = mcd.ProcessImage( image );
// process points
foreach ( Point corner in corners )
{
    // ... 
}
```

To highlight objects' corners as it is showed on the image above, the new **CornersMarker** filter may be used, which can work with any specified corners detection algorithm.

```
// create corner detector's instance
MoravecCornersDetector mcd = new MoravecCornersDetector( );
// create corner maker filter
CornersMarker filter = new CornersMarker( mcd, Color.Red );
// apply the filter
filter.ApplyInPlace( image );
```

**AForge.NET 1.6.0** also introduces some more new features, like Otsu thresholding, initial implementation of Integral Image class, different bug fixed and improvements.

[AForge.NET 1.6.0 Release Notes](http://aforge.googlecode.com/svn/tags/AForge-1.6.0/Release%20notes.txt)

[Information about previous AForge.NET releases](http://code.google.com/p/aforge/wiki/Features)