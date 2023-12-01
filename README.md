# ABB_GoFa_RoboDK
## This is a guide to connect An ABB GoFa robot (CRB15000) to RoboDK.

Please Follow the steps Below:

## 1. Connect to the controller and transfer the socket to the robot.
- Open RobotStudio

![Pasted image 20231127114104](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/4fafda7f-49d5-4f03-9eef-7c3b290f8c18)


- Request write access

![Pasted image 20231129193251](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/583b5d24-ce40-448f-ab49-8d609fe2f916)

![Pasted image 20231129193304](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/0918dc88-57ad-4327-99df-393386781f9a)

- Grant the Access from the Teach Pendant
- Select File transfer

![Pasted image 20231129193503](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/6f1ac63a-abf4-486e-9b56-44fde9893cf2)


- Download RoboDK socket from ABB (Zip included) (https://robodk.com/forum/Thread-RoboDK-driver-for-ABB)
- Extract the zip folder and you will get the RDK_DriverSocket.mod file 
- Change the file extension to **`.modx`**

![Pasted image 20231129194100](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/214735c4-f148-4bb2-88de-7ed42fe43ea5)

- open the socket file and ensure that the  `server_ip` and `port` are the same ports as selected below. 

![Pasted image 20231129195347](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/92ef2ec9-a7b0-4ec0-b4f4-0aca60c7c12b)
![Pasted image 20231129195713](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/eb9608cf-6dae-4d0d-b2c9-d75c1857e1be)

- Extra: if a new tool is to be specified, update tool *progTool*. The intial tool selected is the robot’s *flange* `tool0` (ps: whenever the socket is created the robot will automatically move with tool indicated by the socket, to ensure that the robot’s motion is correctly calculated, make sure its updated).

![Pasted image 20231129195741](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/4082f68d-fd90-4e15-82bf-6f64a1b6a238)

## 2. Allowing the robot’s communication with RoboDK

- In the controller side bar select Controller from the configuration drop down menu

![Pasted image 20231127114246](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/763303ad-5a65-4a99-a270-bb444b65aa88)

- Allow the Rapid Sockets to connect for the robot to communicate with the RoboDK (*you will need write access to change this*).

![Pasted image 20231127114306](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/4f00d935-d036-47f7-a6b5-d268843db876)

- Change the Server Port Number to *514*

![Pasted image 20231127114444](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/c79f5e5a-6059-4724-9933-505e870ec4ca)

-  Restart the controller

## 3. Updating the progam on the teachpendant
- Open the teach pendant.

![Pasted image 20231129194217](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/5fc9381e-a5e3-433a-b7b3-6acd83cf7dba)

- Select `**Code**`

![Pasted image 20231129194318](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/5dc76edf-10f1-4fc0-9f53-2e6e92cce85c)

- Select the **RDK_DriverSocket**

![Pasted image 20231129194423](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/b9ad6b60-60cd-4684-8a0a-4b9ecf501c1f)

- Scroll down to find a routine called **Main** 

![Pasted image 20231129194745](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/b928012d-c9f8-4fae-865e-0b534c131046)

>[!Warning]
> There can be other main routines in other modules (such as the *wizard* for controlling the robot) Make sure any routines that have the word **Main** in any other module are renamed to anything else (such as Main_2 or similar) as the robot will trigger an error in the presence of more than one main routine called `Main`

>[!Warning]
> Never delete any `Main` module in a routine as the module wont work in the future

## 3. Creating the connection
- Select Control 
- Switch To Auto
- Turn the motors on

![Pasted image 20231129195836](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/ea10e8c8-90d4-40fd-b55b-744ce0f04353)
![Pasted image 20231129195938](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/7057b467-87ec-4ba4-b893-911da01d9778)

>[!Warning]
>Reset the Program by pressing reset and start from main so that no remaining commands from other programs are run!

- Press Play

![Pasted image 20231129200049](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/c67368e0-0386-4bf8-943d-071a4140dcde)

## 4. Open RoboDK to connect to the robot.
- Import the Robot in the environment from the library
- Connect to the robot by `Connect Robot`

![Pasted image 20231127114810](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/7eee6662-19bc-4f85-93d5-7252a53d32a3)
![Pasted image 20231127114829](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/8c4e8d5a-2166-4d0b-903c-9b3e0fe853e5)
![Pasted image 20231127114745](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/6e6e0d57-9d8a-4688-961a-2157deca8245)

- Update the connection parameters Connection Parameters

>[!Note]
>Set the **Port** to be *514* and the **Robot IP** to be *192.168.125.1*.  Press more options  and select the Driver **apirobot** (inside more options). 

![Pasted image 20231127114851](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/06c1389a-4a24-4bf1-a907-8079e7b1b984)


![Pasted image 20231127115050 1](https://github.com/NooRetic/ABB_GoFa-connection-with-RoboDK/assets/105431271/86118989-7e89-4598-8f80-e36cbd8dc8a8)


## Done! the robot should be connected to RoboDK.





