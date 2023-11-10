# Lane-Detection

<center>![image](https://github.com/chaza011/Lane-Detection/assets/118681555/f2436ca2-92cd-4d93-8a71-66d1cec25f8a)<center>


If we take a snapshot of our view from the driver's seat of a car, we will see that lanes are such a small part of that image, yet we require autonomous vehicles to see and understand them in order to drive safely. There are also many scenerios where the lanes are not clearly visible such as when they are deteriorated and covered by other vehicles/debris. It is situations like these that an accurate lane detection system is assisting the autonomous vehicle so that it can clearly see the lanes. With this information the vehicle can now pan a path, determine other vehicles positions on the road with respect to itself, and drive safely. With this I will show a variety of different model implementations for lane segmentation using PyTorch. In this case we classify each pixel in an image as lane or not. We also show the Lane Analyzer, a model which takes in the inputs of our lane segmentation model and an object detection model (in this case we use YOLOv8) to determine which lane a given object is in relative to ourself. 

![image](https://github.com/chaza011/Lane-Detection/assets/118681555/94ee9285-d364-4dbc-86ab-a4a219c43a80)


##Models

###Convolutional AutoEncoder

###U-Net

###U-LSTM for Continuous Segmentation

###Vision Transformers for Continuous Segmentation
