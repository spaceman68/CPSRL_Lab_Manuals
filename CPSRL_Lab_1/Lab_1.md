# Lab 1: Optitrack Camera Calibration and Communication 

Authors:

Connell Crawford, 

Alexander Debartolo,

Stephen Kwok-Choon

## Introduction 

Optitrack is platform that allows the tracking of defined rigid body objects in a test environment through the use of optical tracking markers. 

The Space Robotics Laboratory (SRL) is equipped with four (4) optical tracking cameras – the Prime^x 13/13W  cameras.

<figure>
  <img src="./Prime_X_13_Camera.png" alt="Prime X 13 Camera" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Prime X 13 Camera.  </figcaption>
</figure>

Shown in Fig 1. Each camera has a resolution of up to 1.3 Megapixels, with a 3D tracking accuracy of up to 0.20 mm, rated natively up to 240 Frames Per Second, with a maximum frame rate of 1000 Frames Per Second.


<figure>
  <img src="./Motive_Software.png" alt="Motive Software" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 2. A representation of the Motive Software tracking a rigid body object. Lines of sight of each camera is shown.  </figcaption>
</figure>

Shown in Figure 3. is the room layout and the position of the cameras in the room layout. 

<figure>
  <img src="./room_layout_image.png" alt="Room Layout" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 3. Room Layout  </figcaption>
</figure>

### Room Layout (4- Camera Optitrack Array)

Illustrated here in Fig X and X is the floor plan of the SRL as well as an illustration of the line of sight of each camera.

<p align="center">
  <img alt="Light" src="./Floor_Plan_SRL.png" width="40%">
&nbsp; &nbsp;; &nbsp;
  <img alt="Dark" src="./Camera_Illustration.png" width="40%">
</p>
<p align = "center">
  <caption> Figure 4. LEFT: Floor Illustration, RIGHT: Camera View Angle </figcaption>
</p>

### Wiring Data Connection Diagram




Shown here in Fig. 7 is a wiring connection diagram of the cameras, switch, Wi-Fi router as well computer 1 and 2.

<figure>
  <img src="./Connection_Diagram.png" alt="Wiring Connection Diagram of SRL" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 7. Computer 1 (LEFT) and Computer 2 (RIGHT)  </figcaption>
</figure>


Shown here in fig. 8 are the two computers that are connected to the Switch and Optitrack computers. Computer 1 on the left is used to operate Motive software for the Optitrack Camera network.


<figure>
  <img src="./computer_1_and_2.jpg" alt="Computer 1 and 2" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 8. Computer 1 (LEFT) and Computer 2 (RIGHT)  </figcaption>
</figure>


#### Learning Objectives

<div style="color:black; background:lightblue; border: 1px dashed black">

``` 
Objectives: 
1.	Understand how the cameras function and find position
2.	Understand how the Lab Network
3.	Facilitating the use of the Motive Software and Cameras
  a.	Calibrate Cameras
  b.	Create Ridged Bodies
  c.	Broadcast Data from Motive to adjacent software
4.	Detect and display data from Motive in Matlab
5.	Detect and display data from Motive in Simulink
6.	Create 3D simulations in Simulink
7.	Link the data from motive and input into 3D simulink simulation 
``` 
</div>


## 1: Starting Things Up
1.	Set up the space:
  a.	Remove objects blocking the cameras
  b.	During operation and testing, minimize camera line of sight obstructions.
  c.	Remove highly reflective objects and high vis items
2.	Make sure to clear the space of things that block the cameras, and anything that is high visibility or highly reflective as it will add clutter and confusion when operating the cameras.
3.	Turn on both computers, the network switch, and the router. 
  a.	The power switches to turn the network switch and router on are behind the computer monitors. 







































































## 5: Getting Data from the Motive Software into Matlab Simulink 


<div style="color:black; background:lightblue; border: 1px dashed black">

``` 
Objectives: 
1. Download NatNet SDK on Computer 1 
2. Download udp_c_comm_matlab_simulink.zip on Computer 1 
3. Validate and verify correct settings in the FuncMotive function on Computer 1 
4. Update Simulink Sim on Computer 1 
5. Create UDP Send in Simulink Sim using Instrument Control Tool Box 
6. Receive Optitrack Data from Motive to Simulink on Computer 1 
7. Broadcast Optitrack Data from Simulink on Computer 1 
8. Create Simulink Model on your Computer with UDP Receive function. 
9. Receive Optitrack data in Simulink on your Computer. 
10. Document and report on all steps as outlined. 
``` 
</div>

<br> <!-- New Line -->

Or Use Table Method:

| Objectives:  |
| ----------- |
| 1. Download NatNet SDK on Computer 1 |
| 2. Download udp_c_comm_matlab_simulink.zip on Computer 1 |
| 3. Validate and verify correct settings in the FuncMotive function on Computer 1  |


### 5.1 How to get receive Motive data in Simulink using FuncMotive.m on Computer 1 Only. 

1. First download NatNet SDK, which are software libraries and functions that can receive the data from Motive. 

    * Go to https://optitrack.com/support/downloads/developer-tools.html#natnet-sdk or go to https://optitrack.com/ and click on the software tab, then scroll down to NatNet SDK and click learn more, then click download the NatNet SDK.  

    * NOTE: Make sure you are connected to the school Wi-fi network to have internet access. 

    * On this page, you can click on the download link. https://optitrack.com/support/downloads/developer-tools.html  

    * NOTE: the version of NatNet_SDK may be different at the time of downloading of the SDK. 

<figure>
  <img src="./NatNet_SDK_Download.png" alt="NatNetSDK Downlaod Page" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Download NatNetSDK into a folder in your workspace :  Optitrack >  Downloads > Developer Tools > NatNetSDK.  </figcaption>
</figure>


2. Download udp_c_comm_matlab_simulink.zip from Canvas (Provided by the instructor of the lab). 
3. Once the downloads are complete, move NatNet_SDK_4.3.zip and udp_c_comm_matlab_simulink.zip to the same folder -  Optitract folder.
* NOTE: the version of NatNet_SDK may be different at the time of downloading of the SDK. So, you may see numbers other than 4.3. 

4. Make the OptiTrack folder for Computer 1. 

5. Extract/Unzip NatNet_SDK_4.3.zip and udp_c_comm_matlab_simulink.zip each zip file respectively into the OptiTrack folder.  

6. Verify you have these MATLAB Addons  
* Instrument Control Toolbox Addon 
* Aerospace Blockset Addon 
* Simulink Desktop Real-Time Blockset Addon 

<figure>
  <img src="./Instrument_Control_Toolbox_Addon.png" alt="Prime X 13 Camera" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Instrument Control Toolbox Addon .  </figcaption>
</figure>

<figure>
  <img src="./Aerospace_Blockset_Addon.png" alt="Prime X 13 Camera" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Aerospace Blockset Addon.  </figcaption>
</figure>

<figure>
  <img src="./Simulink_Desktop_Real-Time_Blockset_Addon.png" alt="Prime X 13 Camera" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Prime X 13 Camera.  </figcaption>
</figure>
