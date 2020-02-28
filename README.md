# Autonomous driving (Level 1)
## Disclaimer
This document has been created as a requirement for a Capstone project. With less than 3 weeks of development time, the methodology, code etc. might not be of the highest quality and will require review.

## Description
Level 1 Autonomus driving requires a human to have major control over the vehicle while the system provides some information. In this project, we use a camera to capture images of the road from the vehciles perspective, and classify them. There will be some assumptions made and these are listed at the end of this page. 

Here are some of the cases we wish to tackle. (*ACC is 'accelerate', BRAKE is 'brake')
  1. (BRAKE-OBS): There is an obstruction on the road, either a vehicle has stopped or a pedestrian is crossing. 
  2. (BRAKE-RED): The traffic signal is red.
  3. (BRAKE-STOP): There is a stop sign.
  4. (ACC-NOOBS): There is no obstruction.
  5. (ACC-GREEN): The traffic signal turns green.
  
## Data
Our intention was to collect data using a camera attached as a dashcam. However, two major problems exist. 
  1. Most of the data (frames in the video) was shaky causing a serious loss of data. 
  2. The data was not labeled. We don't know what action was taken at the point in the video. Manually labeling these images would be extremely time consuming.
  
Therefore, we will use a simulator like Carla to create our data. By modifying the program, we can get frames of a driving session along with the action taken at a frame-level. 

Here are four frames from Carla along with the (action) data from the vehicle. 

![00043824-20200226-203231-Prem](https://user-images.githubusercontent.com/41816491/75571162-a616f180-5a26-11ea-8ca4-d5b96b742fb3.png)

| Frame         | Speed         | Throttle pos  | Brake pos     |
| ------------- | ------------- | ------------- | ------------- |
| 43824         | 20            | 1             | 0             |

<br/>
<br/>

![00043825-20200226-203231-Prem](https://user-images.githubusercontent.com/41816491/75571198-b4650d80-5a26-11ea-802c-fabf6d052753.png)

| Frame         | Speed         | Throttle pos  | Brake pos     |
| ------------- | ------------- | ------------- | ------------- |
| 43825         | 16            | 0             | 1             |

<br/>
<br/>

![00043826-20200226-203231-Prem](https://user-images.githubusercontent.com/41816491/75571203-b7f89480-5a26-11ea-906e-d74dd41d48f5.png)

| Frame         | Speed         | Throttle pos  | Brake pos     |
| ------------- | ------------- | ------------- | ------------- |
| 43826         | 7             | 0             | 1             |

<br/>
<br/>

![00043827-20200226-203231-Prem](https://user-images.githubusercontent.com/41816491/75571210-bb8c1b80-5a26-11ea-8f41-f9262fa278a9.png)

| Frame         | Speed         | Throttle pos  | Brake pos     |
| ------------- | ------------- | ------------- | ------------- |
| 43827         | 0             | 0             | 1             |

<br/>
<br/>

The vehicle should have registered the traffic light in the frame number 43824 but continues to accelerate, applies the brake in frame numbers 43825 and 43826 thereby reducing its speed, and comes to a complete halt at frame number 43827 at the stop line. 

## Assumptions (and/or fixed parameters)
### Carla parameters
  1. Image size has been set to 400x300
  2. The vehicle and its color has been kept constant
  3. The weather parameter has been set to 'Clear noon' 
  

