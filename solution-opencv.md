I found solution for the OpenCV problem.

Current command to execute conda env is:
```
source activate aind-cv-1
```

The problem was that jupyter notebook didn't see installed versions of Python and OpenCV to conda environment.

I had the following error:
 ``` 
error                                     Traceback (most recent call last)
<ipython-input-6-6947bd6b284f> in <module>()
      1 # Call the laptop camera face/eye detector function above
----> 2 laptop_camera_go()

<ipython-input-5-91aac62a8070> in laptop_camera_go()
      8 def laptop_camera_go():
      9     # Create instance of video capturer
---> 10     cv2.namedWindow("face detection activated")
     11     vc = cv2.VideoCapture(0)
     12

error: /Users/travis/build/skvark/opencv-python/opencv/modules/highgui/src/window.cpp:565: error: (-2) The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script in function cvNamedWindow
 ``` 

I created new conda env, installed jupyter in that environment and updated version of ` opencv-python==3.4.0.12 `. I got the following script:
 ``` 
conda create --name aind-cv-1 python=3.5 numpy tensorflow keras jupyter
source activate aind-cv-1
pip install -r requirements-1.txt
KERAS_BACKEND=tensorflow python -c "from keras import backend"
jupyter notebook
 ``` 
when ` requirements-1.txt ` has content:
 ``` 
opencv-python==3.4.0.12
matplotlib==2.0.0
numpy==1.12.0
pillow==4.0.0
 ``` 

And it perfectly works!

Saúde!
