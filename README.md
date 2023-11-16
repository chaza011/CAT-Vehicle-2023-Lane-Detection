# Lane-Detection

If we take a snapshot of our view from the driver's seat of a car, we will see that lanes are such a small part of that image, yet we require autonomous vehicles to see and understand them in order to drive safely. There are also many scenerios where the lanes are not clearly visible such as when they are deteriorated and covered by other vehicles/debris. It is situations like these that an accurate lane detection system is assisting the autonomous vehicle so that it can clearly see the lanes. With this information the vehicle can now pan a path, determine other vehicles positions on the road with respect to itself, and drive safely. With this I will show a variety of different model implementations for lane segmentation using PyTorch. In this case we classify each pixel in an image as lane or not. We also show the Lane Analyzer, a model which takes in the inputs of our lane segmentation model and an object detection model (in this case we use YOLOv8) to determine which lane a given object is in relative to ourself. 

![image](https://github.com/chaza011/Lane-Detection/assets/118681555/2de4c829-3c42-4fd0-accc-c282b00496e5)


## Models
Here we will show/explain the achitecture for the lane segmentation models as to aid in any confusion when reading the code we provide. Here we only briefly go over the general outline of the model and do not go into too much depth. For more information on CNNs please see: https://github.com/chaza011/Intro-to-Machine-Learning. Below is the flow of our system: we first send an input image through our lane and object detection models and combine the output to be sent to the lane analyzer. 

<p align="center">
  <img src="https://github.com/chaza011/Lane-Detection/blob/main/Screenshot%202023-11-10%20101525.png" 
  alt="The lane analysis process: we first send our image to our lane segmentation model and object detector. Then we combine both outputs and send it to the Lane Analyzer" width="1000"/>
</p>

### Convolutional AutoEncoder
The convolutional autoencoder uses convolution layers to learn valuable features from that image as it encodes it into a lower dimensional latent space. The decoder then uses the encoding and brings it back to its original dimensionality, but now in such a way that it satisifes an objective function, which in this case is correctly classifying each pixel as 0 (not lane) or 1 (lane). 
### U-Net

The U-Net utilizes the autoencoder architecture, but it also sports skip connections that take the output from each encoder block and concatenate them to the inputs for its corresponding decoder block. The skip connections maitain feature information from different resolutions in the encoding process. The U-Net has been shown to be successful in segmenation tasks as it was originally developed for medical segmentation. For more information please read the original paper: https://arxiv.org/abs/1505.04597. 

### U-LSTM for Continuous Segmentation

Driving is a continuous task, and we often use our memory of where things are on the road as we drive. For example, we do not forget where the lane is just because a car is covering it in a particular instance. This is important as a model that does not make use of previous frame information will have more trouble accurately predicting lanes for challenging scenerios such as curvature and occlusion of lanes. With this we show an implementation of a U-Net with a Long-Short-Term-Memory (LSTM) component as the bottleneck. The LSTM learns temporal information and now gives the model access to previous frame information when making a prediction. 

### Vision Transformers for Continuous Segmentation

Transformers have shown to be state of the art in vision-based tasks with vision transformer models. We decided to create a vision transformer (ViT) network that utilizes a pre-trained ViT for processing indivigual frames and then a second vision transformer we made to process temporal information between frames before making a decision. In this network each frame is processed by the first ViT and then added to a sequence of frames which are processed by the temporal model. 
