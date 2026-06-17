# Axis controller

## Preambule
WRSimulator allows the insertion of axis controllers into folios. The simulated axis controller provides a limited emulation of the IAI SCONS2 axis controller. ([SCON2-CE0401-1.1A.pdf](assets/SCON2-CE0401-1.1A.pdf))

The example **us43-demo_controller_axis_CODESYS.xrs** demonstrates the implementation of an **IAI-SCON2**  axis controller for controlling the positioning of a lifting table.

### CODESYS axis controller simulation
![](assets/axis_controller.png)

### Quick description


- The CODESYS ControlWin 64 virtual PLC is connected to the axis controller simulated by WRSimulateur via Modbus TCP-IP
- The interaction between the PLC and the controller is handled through an exchange table consisting of 5 words (e.g., %QW5.0 to %QW5.2 and %IW5.0 to %IW5.1 in this example).
- The program in the project  **us43-demo_controller_axis_CODESYS.project** adjusts the control bits of the **axis_ctrl** register in the controller based on the state of the buttons connected to its inputs.
- The speed and setpoint are set by the program (lines 9 and 10 of the program below).
- You can test the behavior of the mobile table positioning by forcing values in the **axis_setpoint** and **axis_speed** registers.
- The axis controller includes a PID position control loop. The PID gains (Kp, Ki, Kd) are tunable via the Kp, Ki, and Kd buttons.
- The axis position can be visualized on the plotter (grapher module) using the **axis_position**.

### CODESYS axis controller program   
![](assets/axis_controller_CODESYS.png)



## Parameters

The addresses of the PLC words used in the tables below are provided as examples. Different addresses can be selected in the virtual PLC mapping.

![](media/modbus_modules.png)

|Default parameter      |Description                    |
| ------------------ | ------------ |
|In = 10 A|Axis Controller caliber|
|axis_ctrl = %QW5.0|Control bits|
|axis_setpoint = %QW5.1 |Position setpoint |
|axis_speed = %QW5.2 |Axis movement speed in %|
|axis_status = %IW5.0 |Axis controller status|
|axis_position = %IW5.1 |Axis position (%)|
|home_point = 0 mm |Home position value (mm)|
|max_position = 700 mm |Max position value (mm)|

|axis_ctrl      |Bit descriptions                    |
| ------------------ | ------------ |
|set servo (%QW5_0.0)|Enables the axis controller operation [False,True]|
|stop move (%QW5_0.1)|Stop motion request [False,True]|
|goto home (%QW5_0.2)|Requests return to home position [False,True]|
|goto setpoint (%QW5_0.3)|Requests positioning to setpoint [False,True]|
|raz default (%QW5_0.4)|Requests fault reset (overload) [False,True]|

|axis_status      |Bit descriptions                 |
| ------------------ | ------------ |
|setpoint_reached (%IW5.0)| Setpoint position reached [False,True]|
|homepoint_reached (%IW5.1)| Home position reached [False,True]|
