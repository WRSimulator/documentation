# Programmable Logic Controller
## Preamble
- The simulator integrates a physical or virtual PLC into a folio.
- Communication with the PLC is carried out using the [Modbus/Tcp-IP] protocol (modbus.md)
    - with the local IP address (127.0.0.1) of the Modbus server integrated into the virtual PLC,
    - with the static IP address of the Modbus server integrated into the physical PLC connected to an Ethernet network.
- This solution makes it possible to use the usual PLC programming tools.
- Exchange logic **client (master) (simulator) <-> server (slave) (api)**, periodically :
    - the Modbus client (simulator) sends a request to write the simulated SAP inputs to the Modbus server (PLC),
    - the PLC calculates the state of the SAP outputs according to its program and the state of the inputs received,
    - the Modbus client (simulator) sends a request to read the outputs calculated by the program to the Modbus server (PLC),
    - the simulator updates the SAP status.
- PLCs tested :
    - **M221** Schneider Electric function codes 3,16 and 23, integrated Modbus server
    -  **M340** Schneider Electric function codes 3 and 16, integrated modbus server
    -  **Unilogic** Unitronics function codes 3,16 and 23, Modbus server configuration required

![](media/unilogic.png)
  
- **CODESYS Control Win** CODESYS 3.5, codes 3,16 et 23, Modbus server configuration required
  
    ![](en/media/codesys00.png)
    ![](en/media/codesys0.png)
    ![](en/media/codesys1.png)
    ![](en/media/codesys2.png)
    ![](en/media/codesys3.png)

  - Only holding registers are used.
    - 48 registers (16-bit word) are allocated:
        - 24 registers for outputs, table start address: **QW_address** = 0,
        - 24 registers for inputs, table start address: **IW_address** = 24.
    - The variables used in the program are assigned directly in the Modbus I/O mapping.
    - The parameter **writable** is ticked to authorize the server to write to the 24 output registers **%QWx.y** of modules M0 to M5.  



## Virtual PLC front panel

![](en/media/modbus_modules.png)

- Each I/O module integrates four input words and four 16-bit output words.
- These words can be specified as :
    - analog' inputs or outputs,
    - digital inputs or outputs.
- Finally, each module can manage :
    - up to 64 digital inputs and 64 digital outputs,
    - a mix of digital and analog I/Os, e.g. module 0:
        - %QW0.0 -> 16-bit word for an 'analog' output
        - %QW0.1 -> 16 bits usable for 16 digital outputs
        - %IW0.0 -> 16 bits usable for 16 digital inputs

The following examples illustrate the use of dE/S modules.


## M221 Elevator example
Files :

- us15 - demo_elevator_M221.xrs
- us15 - demo_elevator_M221.smbp (**Ecostruxure**)

### Preparation side Simulator

![](media/lift_example.png)

- Elevator control requires 8 digital inputs and 4 digital outputs. An M221 type TM221CE16R can be used, with 9 digital inputs and 7 relay outputs.
- Addressing of digital inputs: %I0.0, %I0.1, %I0.2, %I0.3, %I0.4, %I0.5, %I0.6, %I0.7, %I0.8
- Output addressing: %Q0.0, %Q0.1, %Q0.2, %Q0.3, %Q0.4, %Q0.5, %Q0.6
- This example implements 8 input objects and 4 output objects, identifying them with standard PLC addresses.


**Input assignment**

|                      |                                              |   |
| -------------- | ------------------------------ |--|
|address|mnemonic|comment|
| %I0.0|E3|appel étage 3|
|%I0.1|E2|appel étage 2|
|%I0.2|E1|appel étage 1|
|%I0.3|P1|cabine à létage 1|   
|%I0.4|P2|cabine à létage 2|   
|%I0.5|P3|cabine à létage 3|
|%I0.6|PF|porte cabine fermée|   
|%I0.7|PO|porte cabine ouverte|

**Output assignment** 

|                      |                              |   |
| -------------- | ------------------ |--|
|address|mnemonic|comment|
|%Q0.0|OUVRIR|Open door|   
|%Q0.1|FERMER|Close door
|%Q0.2|DESCENDRE|go down cab|
|%Q0.3|MONTER|go up cab|

### Preparation side **EcoStruxure** 


The complete program **us15 - demo_elevator_M221.smbp** is available in the : ![](media/image89.png)


Mapping of input/output tables to the exchange table set at start address %MW400 [see modbus mapping](modbus.md):
  
|                      |                                    |   |   |
| -------------- | -----------------------|--|--|
|adress| MODBUS mapping|mnemonic|comment|
| %I0.0  |%MW500 :X0|E3|call stage 3|  
| %I0.1  |%MW500 :X1|E2|call stage 2|
| %I0.2  |%MW500 :X2|E1|call stage 1|
| %I0.3  |%MW500 :X3|P1|elevator cab on floor 1|
| %I0.4  |%MW500 :X4|P2|elevator cab on floor 2|
| %I0.5  |%MW500 :X5|P3|elevator cab on floor 3|
| %I0.6  |%MW500 :X6|PF|cab door closed|
| %I0.7  |%MW500 :X7|PO|cab door open|

|                      |                    |   |   |
| -------------- | ------------ |--|--|
|adress| MODBUS mapping|mnemonic|comment|
|%Q0.0|%MW400 :X0|OUVRIR|Open cab door|
|%Q0.1|%MW400 :X1|FERMER|Close cab door|
|%Q0.2|%MW400 :X2|DESCENDRE|go down cab|
|%Q0.3|%MW401 :X3|MONTER|go up cab|


In the **Programming ->Tools ->Symbols list** tab, you'll find the input/output assignments that correspond to the tables above:
![](media/lift_symbol_list.png)

**PLC program**
![](media/lift_sfc.png)
![](media/image95.png)
![](media/image96.png)


Start the controller **BEFORE** starting the simulator by activating the **Start simulation** and **Start controller** buttons in the EcoStruxure commissioning tab.

## CODESYS analogs I/O 

Files :

- us41 - demo_analog_I-O_CODESYS.smbp
- us41 - demo_analog_I-O_CODESYS.project  (**CODESYS 3.5**)

[Use CODESYS with the simulator](assets/CODESYS_LAUNCH.mp4)

### Preparation side Simulateur

- The diagram implements : 
    - three analog inputs:
        - %IW1.0 connected to 4-20 mA sensor B2
        - %IW1.1 connected to 4-20 mA sensor B1 
        - %IW1.2 connected to 0-10 V sensor AU1
    - two analog outputs:
        - %QW2.0, 0-20 mA current output
        - %QW2.1, voltage output 0-10 v

- The grapher [Grapher](grapher.md) is parameterized to display the evolution of the %QW2.0 output
    - Vqw2_0.value.5
        - Vqw2_0 -> voltmeter name
        - value -> display of measured value
        - 5 -> voltmeter rating (250 * 20e-3)* 20e-3)

![](en/media/saw.png)

- The program in the controller adjusts the sawtooth period using the potentiometer on the AU1 sensor connected to %IW1.2.

![](en/media/es_codesys.png)

### Preparation side  **CODESYS**

- Variables are assigned directly in the modbus I/O mapping [Modbus configuration](plc.md) 
    - %IW1.0 -> IW1_0
    - %IW1.1 -> IW1_1
    - %IW1.2 -> IW1_2

- ST code with all I/O registers for visualization
![](en/media/es_source_codesys.png)

- CODESSYS running
    - F11 (create code)
    - Alt-F8 (connect) the CODESYS Control Win Systray controller must be running 
    - F5 (start)

![](en/media/es_exec_codesys.png)




## CODESYS box sorting 

Files :

- us42 - demo_box_sorting_CODESYS.smbp
- us42 - demo_box_sorting_CODESYS.project  (**CODESYS 3.5**)

[Use CODESYS with the simulator](assets/CODESYS_LAUNCH.mp4)

### Preparation side Simulateur
![](en/media/tri_codesys.png)

### Preparation side  **CODESYS**

- Variable assignment is done directly in the modbus I/O mapping [Modbus configuration](plc.md) 
![](en/media/tri_affec0_codesys.png)
![](en/media/tri_affec1_codesys.png)

- SFC preparation
![](en/media/tri_source0_codesys.png)

- ST code with all I/O registers for visualization
![](en/media/tri_source1_codesys.png)

- CODESSYS at runtime
![](en/media/tri_exec0_codesy.png)
![](en/media/tri_exec_codesys.png)


## Building a PLC object

- A PLC is built with the elementary objects :
    - input# for digital inputs,
    - output# for digital outputs,
    - analog_input# for analog inputs,
    - analog_output# for analog outputs,
    - plc_supply# for PLC power supply.
- All I/Os have the plc_supply object as their parent, in order to link the supply of these I/Os to the PLC power supply.
- The MODBUS server is implicitly attached to the PLC in place in the schematic.
- Only one PLC can be placed in the schematic.
- Examples of PLCs are available in the folder [blocs_simulables](library.md), using the WinRelais command 'Open a block'.

![](media/image104.png)
All these automaton footprints can be adjusted and modified as required.

## Logic Input/Output
|input, output|library _api|
| -----------------| -----------------------|
|%Ir.v or %Qr.v|r = [0,5] v = [0,31] |
|parent =         | object name **plc_supply#**|

![](media/io_tor.png)

## Analog inputs
|analog_input|library _api|
| ---------------| ----------------------------------------------------------|
|%IWr.v           |r = [0,5] v = [0,3] |
|parent =         | object name **plc_supply#**|
|input_type =   | U  ou  I|
|input_range = |(min,max) V [-10,10] V or (min,max) mA [0, 20] mA|
|input_scale = |min,max   [-32768, 32767]|

![](media/analog_inputs.png)

## Analog Outputs
|analog_output|library _api|
| ---------------| ---------------------------------------------------------|
|%QWr.v           |r = [0,5] v = [0,3]|
|parent =         |   object name **plc_supply#**|
|output_type =   | U  or  I|
|output_range = |(min,max) V [-10,10] V or (min,max) mA [0, 20] mA|
|output_scale = |min,max [-32768, 32767]|

![](media/analog_outputs.png)
