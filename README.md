# ABB_GoFa_RoboDK
## This is a guide to connect An ABB GoFa robot (CRB15000) to RoboDK. It is part of my work completed during my PhD at Glasgow Caledonian University 2020-_present_

Please Follow the steps Below:

## 1. Connect to the controller and transfer the socket to the robot.
- Open RobotStudio

![Pasted image 20231127114104](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/b31b962f-2f79-4260-a8a1-69b3077f248b)


- Request write access

![Pasted image 20231129193251](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/8acbbff1-63c7-4df2-8865-b670ebb65bef)

![Pasted image 20231129193304](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/8cad3f3f-db5c-4686-8d49-c6b013fd36e8)

- Grant the Access from the Teach Pendant
- Select File transfer

![Pasted image 20231129193503](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/2f404752-3b47-4e62-b60a-fbbd24d64b4a)


- Download RoboDK socket from ABB (Zip included) ([https://robodk.com/forum/Thread-RoboDK-driver-for-ABB] this is the link containing the files offered by the Robotic Software Manager **Jérémy Brouillard**)
- Extract the zip folder and you will get the RDK_DriverSocket.mod file 
- Change the file extension to **`.modx`**

![Pasted image 20231129194100](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/c2730c36-b638-48cc-a8f7-1ac22a1a7f54)

- open the socket file and ensure that the  `server_ip` and `port` are the same ports as selected below. 

![Pasted image 20231129195347](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/7893ec37-ff1f-4f88-b1ea-d68560f2b4c3)
![Pasted image 20231129195713](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/c9d9fdeb-2681-4a2a-82fb-9aac7a7ec340)

- Extra: if a new tool is to be specified, update tool *progTool*. The intial tool selected is the robot’s *flange* `tool0` (ps: whenever the socket is created the robot will automatically move with tool indicated by the socket, to ensure that the robot’s motion is correctly calculated, make sure its updated).

![Pasted image 20231129195741](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/c7ce0c33-38b0-4a6e-a8e8-33243e7b7c3f)

## 2. Allowing the robot’s communication with RoboDK

- In the controller side bar select Controller from the configuration drop down menu

![Pasted image 20231127114246](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/a9cc3a04-c56e-4f68-9001-cfde353e7e9c)

- Allow the Rapid Sockets to connect for the robot to communicate with the RoboDK (*you will need write access to change this*).

![Pasted image 20231127114306](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/617fa478-0152-4f05-ba54-728ec70884f2)

- Change the Server Port Number to *514*

![Pasted image 20231127114444](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/0cdde9b0-bbdf-4d82-af8d-dcce178f8f04)

-  Restart the controller

## 3. Updating the progam on the teachpendant
- Open the teach pendant.

![Pasted image 20231129194217](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/f10a97e3-da98-435b-bd89-133a4e20f5b2)

- Select `**Code**`

![Pasted image 20231129194318](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/351c82ee-4231-400e-9afd-151b0bb59369)

- Select the **RDK_DriverSocket**

![Pasted image 20231129194423](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/a1836cc5-1701-48cc-bad3-ec310eb41daf)

- Scroll down to find a routine called **Main** 

![Pasted image 20231129194745](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/3b06b639-f8f0-4c9b-a12c-523600e17c64)

>[!Warning]
> There can be other main routines in other modules (such as the *wizard* for controlling the robot) Make sure any routines that have the word **Main** in any other module are renamed to anything else (such as Main_2 or similar) as the robot will trigger an error in the presence of more than one main routine called `Main`

>[!Warning]
> Never delete any `Main` module in a routine as the module wont work in the future

## 3. Creating the connection
- Connect an Ethernet cable between the robot and the computer (use the ethernet ports available in the robot's unit)
- Select Control 
- Switch To Auto
- Turn the motors on

![Pasted image 20231129195836](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/3b978239-3928-4c41-880c-b6d53b436f0e)

![Pasted image 20231129195938](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/27f57f57-ceea-4878-87a0-c0ea7c352de9)

>[!Warning]
>Reset the Program by pressing reset and start from main so that no remaining commands from other programs are run!

- Press Play
  
![Pasted image 20231129200049](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/02c89daa-623c-4f90-8297-382678a9999a)

## 4. Open RoboDK to connect to the robot.
- Import the Robot in the environment from the library
- Connect to the robot by `Connect Robot`

![Pasted image 20231127114810](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/865939f5-4c9f-46be-bb19-3897e9846909)
![Pasted image 20231127114829](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/5c562ef6-7169-47bc-b357-44e5b17e7f98)
![Pasted image 20231127114745](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/28ca98b3-e111-40fe-8b1d-f80d1ad4e7ac)

- Update the connection parameters Connection Parameters

>[!Note]
>Set the **Port** to be *514* and the **Robot IP** to be *192.168.125.1*.  Press more options  and select the Driver **apirobot** (inside more options). 

![Pasted image 20231127114851](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/709cef97-2177-4a62-8bcd-937fc3c6f117)

![Pasted image 20231127115050 1](https://github.com/NooRetic/ABB_GoFa_RoboDK/assets/105431271/43258a85-cd1e-465f-92b8-9bbc03296980)

## Done! the robot should be connected to RoboDK.



## References
- RoboDK Inc. (2023). RoboDK driver for ABB - RoboDK Documentation. [https://robodk.com/doc/en/Robots-ABB-RoboDK-driver-ABB.html].
- RoboDK driver for ABB. (2023). Retrieved December 5, 2023, from [https://robodk.com/forum/Thread-RoboDK-driver-for-ABB].

