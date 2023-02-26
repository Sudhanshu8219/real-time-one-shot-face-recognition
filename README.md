# real-time-one-shot-face-recognition
Realtime One Shot Face recognition using Deep Convolutional Neural Network

Introduction
The task is to detect whether a face is present in database or not.

This seems very straight forward, Train a Convolutional Neural Network model using labelled faces present in database. (label may be name, regitration no., mobile or email). and use this model to identify those faces.

But! What is problem with this method?
Suppose a new person joins or leaves the organisation then we will have to retrain our CNN model with updated labelled faces. If we retrain the model again it will consume time and computational resources again to train model which is not feasible for big organisation.

How to takle this problem?
To overcome this problem we use a one-shot face recognition CNN model in which we train it in such a way it will check whether two images are of same person or not. So model will compare the detected face in with all faces in database.

So whenever a person joins or leaves the organisation we just have to update our database.

Steps involves in One-shot face recognition
Face detection
Posing and projecting face
Face regonition (Face matching)
Face Detection
Detecting the face using one of face detection algorith i.e. Viola Jones Algorithm, Histogram of Oriented Gradients and cropped out the deteted faces in a video frame or image.



Posing and projecting face
If the detected face is somewhat rotated or tilted, then we try to align the face in frontal pose using Facial landmarks. This improves the face recognition accuracy very well.



Facial Landmarks



Face Alignment

Face Matching
In this final step we use a DCNN model like Resnet50, Facenet, mobilenet, Alexnet, VGG net, etc to encode preprocessed image into a 128 size floating vector. This 128 size floating vector is use the calculate the Euclidean or Cosine distance between two images. If the distance is below a threshold limit we assume those images of same person.



128 size encoded vector from Image

Setup
Prerequisite
Please check requirements.txt for version of packages.

Python >=3.7.0
Numpy
Dlib
OpenCV
Pillow
Tensorflow (For Notebook only)
NOTE: To install Dlib on windows search how to install dlib on windows and follow instructions.

How to run?
Just put all the images in images folder from which you want to identify faces. (The name of image will be used as label without extension)
Now Run the following command to start the app.
python main.py
Now a new window will open where you can see yourself.
To close that window press q.
How to use mobile camera?
Download IP Webcam app on you mobile device.
Now in setting of app decrease the resolution to 640x480 and quality to 50 for better experience.
Now start the server in app.
An IP will be show on screen like http://192.168.***.***:8080, Copy this and paste it on main.py line 139 along like this http://192.168.***.***:8080/shot.jpg and uncomment video_capture class.
Now run the python command given above to connnect to mobile camera.
Demo of real time face recognition
demo-video
