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

## Carla (about and installation)
  1. The simulator can be found at http://carla.org/. 
  2. We are using the release version 0.9.5 as it has an experimental version for Windows. The download link for this is https://github.com/carla-simulator/carla/releases/tag/0.9.5. 
  3. The prerequisites for a Windows system can be found at https://carla.readthedocs.io/en/latest/how_to_build_on_windows/
  4. Start at the core concepts (https://carla.readthedocs.io/en/latest/core_concepts/)
  5. This link (https://carla.readthedocs.io/en/latest/python_api/) is handy for the understanding of Python APIs
  
## Running Carla and changes to generate data
After unzipping the contents to a folder, you should have the following files available 

![image](https://user-images.githubusercontent.com/41816491/75577347-d616c280-5a2f-11ea-931d-95cabb92a80a.png)

Execute the application 'CarlaUE4' (which is the Unreal Engine) and then under \PythonAPI\examples folder you will find a buch of python script files. A few of the interesting ones are 
  1. automatic_control.py: This program will spawn a vehicle at a random point on the map, generate a destination, and start controlling the vehicle to the desctination. It should follow all rules like traffic and obstructions and not get into any collisions. 
  2. manual_control.py: Spawns a vehicle at a random position and gives the user control over the vehicle. There are options mapped to keys which will give you a lot more control over the simulation. 
  3. spawn_npc.py: will spawn a number of vehicles on the road which will follow the road rules. 
  4. tutorial.py: shows you how a program should be written to use Carla efficiently. Note that not all the functions are shown but it is an excellent spot to get started with understanding the simulator.

### Changes to generate the data
We use the file [manual_control.py](../master/code_files/manual_control.py) to generate the data. This program has a couple of options that help us with this. The first is that this program has the ability to record i.e. on activating it, frames are stored in the folder \PythonAPI\examples\_out. The second interesting ability is that you can switch on autopilot. This controls the vehicle following the rules of the road. The one thing that the program does NOT do is return vehicle state at a frame level. For this, we have made some changes in the program ([manual_control.py](../master/code_files/manual_control.py)) to retrive them and return a CSV file. The changes have been marked with the comment lines. 

## Assumptions (and/or fixed parameters)
### Carla parameters
  1. Image size has been set to 400x300
  2. The vehicle and its color has been kept constant
  3. The weather parameter has been set to 'Clear noon' 
  
## Citations, credits, and sources
1. carla.org 
  

