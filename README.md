# Autonomous driving (Level 1)
## Disclaimer
This document has been created as a requirement for a Capstone project. With less than 3 weeks of development time, the methodology, code etc might not be of the higest quality and requires review.

## Description
Level 1 Autonomus driving requires a human to have major control over the vehicle while the system provides some information. In this project, we use a camera to capture images of the road from the vehciles perspective, and classify them.

Here are some of the cases we wish to tackle
  1. (BRAKE-OBS): There is an obstruction on the road, either a vehicle has stopped or a pedestrian is crossing. This is a 'brake' class.
  2. (BRAKE-RED): The traffic signal is red.
  3. (BRAKE-STOP): There is a stop sign.
  4. (ACC-NOOBS): There is no obstruction. This is an 'accelerate' class.
  5. (ACC-GREEN): The traffic signal turns green.
  
## Data
Our intention was to collect data using a camera attached as a dashcam. However, two major problems exist. 
  1. Most of the data (frames in the video) was shaky causing a serious loss of data. 
  2. The data was not labeled. We don't know what action was taken at the point in the video. Manually labeling these images would be extremely time consuming.
  
Therefore we intend on using a simulator like Carla to create our data. 
By modifying the program, we can get a frame of a driving session along with the action taken at the frame. 

Here is an example of a frame from Carla. 
![Example - red light](https://user-images.githubusercontent.com/41816491/75568209-deb3cc80-5a20-11ea-8ca6-7de013815a3f.png)
Notice that the traffic signal in the direction of travel is red. The car should stop and this image should be classified as 'BRAKE-RED'.
