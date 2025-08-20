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

<br> <!-- New Line/Paragraph -->

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
<!--Picture 1-->
<figure>
  <img src="./Instrument_Control_Toolbox_Addon.png" alt="Instrument Control Toolbox MATLAB Addon" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Instrument Control Toolbox Addon.  </figcaption>
</figure>
<!--Picture 2-->
<figure>
  <img src="./Aerospace_Blockset_Addon.png" alt="Aerospace Blockset MATLAB Addon" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Aerospace Blockset Addon.  </figcaption>
</figure>
<!--Picture 3-->
<figure>
  <img src="./Simulink_Desktop_Real-Time_Blockset_Addon.png" alt="Simulink Desktop Real-Time Blockset MATLAB Addon" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Simulink Desktop Real-Time Blockset Addon.  </figcaption>
</figure>

7. Reconnect to the Router:  SPACE_ROBOTICS_LAB 
8. In MATLAB, open the Funcmotive.m file in the udp_c_comm_matlab_simulink folder.
<figure>
  <img src="./FuncMotive_Start.png" alt="FuncMotive_Unedited" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. This is what you should see when you open the FuncMotive.m file in Matlab.   </figcaption>
</figure>

9. Scroll down the file until you find the line of code that is trying to point to the NatNet_SDK_X. Find this line (Line 98): dllpath = fullfile(... 
<figure>
  <img src="./" alt="Updating FuncMotive dllPath line." width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Need to update the dllPath.    </figcaption>
</figure>

In the version that you have unzipped it is: 

* dllPath = fullfile('c:','Users','ORION1','Desktop','Stephen KWOK CHOON DO NOT TOUCH','Motive Streaming','NatNet_SDK_2.8','NatNetSDK','lib','x64','NatNetML.dll'); 

* The dllPath has to point to the NatNetML.dll file located inside the NatNet_SDK_X.X  developer folder that you have downloaded. 


10. Open the NatNet_SDK_4.3 folder and go down the path > NatNetSDK > lib > x64 

* NOTE: the version of NatNet_SDK may be different at the time of downloading of the SDK. 

* Your path may look like this: C:\Users\skwokcho\Desktop\Optitrack\NatNet_SDK_4.3\NatNetSDK\lib\x64

11. Copy the path at the top of the folder.  

<figure>
  <img src="./dllPath_file_explorer.png" alt="Selecting Path in File Explorer" width: 100%;
  height: auto;
  /* Magic! */
  max-width: 50vw;>
  <figcaption>Figure 1. Showing two different ways to find the file path for the NatNetML.dll file.     </figcaption>
</figure>






<!-- Im doing this first  -->
<br> <!-- New Line/Paragraph -->
<br> <!-- New Line/Paragraph -->
<br> <!-- New Line/Paragraph -->
<br> <!-- New Line/Paragraph -->
<br> <!-- New Line/Paragraph -->
<br> <!-- New Line/Paragraph -->

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