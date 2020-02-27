# Autonomous driving (Level 0)
## Disclaimer
This document has been created as a requirement for a Capstone project. With less than 3 weeks of development time, the methodology, code etc might not be of the higest quality and requires review.

## Description
We intend on using image recognition to classify an image with one of the two classes. These classes are 'accelerate' and 'brake'.

## Data
Our intention was to collect data using a camera attached as a dashcam. However, two major problems exist. 
  1. Most of the data (frames in the video) was shaky causing a serious loss of data. 
  2. The data was not labeled. We don't know what action was taken at the point in the video.
  
Therefore we intend on using a simulator like Carla to create our data. 
By modifying the program, we can get a frame of a driving session along with the action taken at the frame. 

