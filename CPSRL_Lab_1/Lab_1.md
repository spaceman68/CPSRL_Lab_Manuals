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

Shown in Fig X. is the room layout and the position of the cameras in the room layout. 

<figure>
  <img src="./room_layout_image.png" alt="Room Layout" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 3. Room Layout  </figcaption>
</figure>










































































## 5: Getting Data from the Motive Software into Matlab Simulink 

<div style="color:black; background:lightblue; border: 1px dashed black">
```
| Objectives:  |
| ----------- |
| 1. Download NatNet SDK on Computer 1 |
| 2. Download udp_c_comm_matlab_simulink.zip on Computer 1 |
| 3. Validate and verify correct settings in the FuncMotive function on Computer 1  |


```
</div>


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

   

