A collection of experiments with the Leap Motion Controller to use it as a gesture based input device for Windows and a rudimentary 3D scanner

### Installation
* Clone the repo or download the zip
* Make sure you have the Leap SDK installed
* run `pip install -r "requirements.txt"`
* 3D-Scanning works with Python 3.6 but Leap Motion doesn't provide bindings for 3.6 so copy over the files from the `lib` folder to `site-packages`
* You can also generate python bindings for any version of python using the instructions [here](https://support.leapmotion.com/hc/en-us/articles/223784048-Generating-a-Python-3-3-0-Wrapper-with-SWIG-2-0-9)

### Usage
#### LeapMouse
*  `cd` to the `LeapMouse` folder
* run `python LeapMouse.py`
* The coordinates of the palm are used to move the mouse pointer around
* A pinch between any finger and the thumb simulates a click
* If the ring finger and pinky are not extended (Like the German hand gesture for the number three), the script enters scrolling mode and tilting the palm scrolls up and down. Moving the palm front and back zooms into and out of the screen
* Make a fist with the palm pointing left to grab the active window and move it around the screen
* Moving the hand in a circle of radius > 50 mm in clockwise/anticlockwise direction increases/decreases the master volume

> Note:  LeapMouse.py works only with Windows and Python 2.7

##### Dependencies
* Pywin32 - Win32 API for Python
* comtypes - Pure Python COM package

#### 3D Scanning

*  `cd` to `3D-Scanning` and run `python image_correction.py` to see a point cloud generated by OpenCV's stereoscopic 3D reconstruction routines. I've used PyQtGraph to render the cloud as Matplotlib was really slow for plotting 640 * 240 points in 3D space. You can read more about 3D reconstruction using OpenCV [here](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_calib3d/py_table_of_contents_calib3d/py_table_of_contents_calib3d.html)
* `camera_constants.py` contains the required camera calibration parameters like the intrinsic/extrinsic and reprojection matrices.  [This](http://www.cs.toronto.edu/~fidler/slides/2017/CSC420/lecture10.pdf) is an excellent source on camera models and calibration. The calibrated parameters aren't optimal so the point cloud has quite a bit of noise. I've had to make do with some of the calibrated parameters I found [here](https://www.ripublication.com/ijaer17/ijaerv12n16_69.pdf)

##### Dependencies
* PyQtGraph

### Screenshots
![img](https://i.imgur.com/7u83hjH.gif)

Point cloud of my hand

![img](https://i.imgur.com/ayRYZRi.gif)

fingertip and palm coordinates from plot_fingers.py

![img](https://i.imgur.com/SXojja9.png)

a 3D scan of a coffee cup

#### Contributing
All contributions are welcome, especially for improving the camera calibration