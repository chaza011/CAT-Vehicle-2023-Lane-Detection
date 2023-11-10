# Lane-Detection

![image](https://github.com/chaza011/Lane-Detection/assets/118681555/2de4c829-3c42-4fd0-accc-c282b00496e5)

If we take a snapshot of our view from the driver's seat of a car, we will see that lanes are such a small part of that image, yet we require autonomous vehicles to see and understand them in order to drive safely. There are also many scenerios where the lanes are not clearly visible such as when they are deteriorated and covered by other vehicles/debris. It is situations like these that an accurate lane detection system is assisting the autonomous vehicle so that it can clearly see the lanes. With this information the vehicle can now pan a path, determine other vehicles positions on the road with respect to itself, and drive safely. With this I will show a variety of different model implementations for lane segmentation using PyTorch. In this case we classify each pixel in an image as lane or not. We also show the Lane Analyzer, a model which takes in the inputs of our lane segmentation model and an object detection model (in this case we use YOLOv8) to determine which lane a given object is in relative to ourself. 

<p align="center">
  <img src="https://github.com/chaza011/Lane-Detection/blob/main/Screenshot%202023-11-10%20101525.png" 
    alt="The lane analysis process: we first send our image to our lane segmentation model and object detector. Then we combine both outputs and send it to the Lane Analyzer" width="400"/>
</p>

## Models

### Convolutional AutoEncoder

### U-Net

### U-LSTM for Continuous Segmentation

### Vision Transformers for Continuous Segmentation
