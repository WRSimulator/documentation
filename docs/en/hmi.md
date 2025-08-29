# Human Machine Interface

![](media/hmi1.png)

- hmi components can be modified in WinSymbole.
- Variants of ihm components can be created by adding the suffix **#my variant** after the component root. Example:
![](media/hmi2.png)


## Light
|voyant|library /_hmi|
| -------------- | --------------------------------------------- |
|texture_name =|foreground texture in png format|
|texture_name2 =|optional background texture in png format|

## Push button / Slide button

|pushbutton, slide_button |library /_hmi|
| -------------- | --------------------------------------------- |
|latching =| latch the button [0,1] [False,True]|
|texture_name =|foreground texture in png format|
|texture_name2 =|optional background texture in png format|
|state =|fixes active/non-active button state, only if snap = True|

## Switch
|switch_2pos, switch_3pos |library /_hmi|
| -------------- | --------------------------------------------- |
|latching =| allow latching [0,1] [False,True]|
|texture_name =|foreground texture in png format|
|texture2_name =|optional background texture in png format|
|state =|0,1,2: switch position, only if latching parameter = True|

## Potentiometer
|rotating_knob, horizontal_linear_knob, vertical_linear_knob|library /_hmi|
| -------------- | --------------------------------------------- |
|alpha =|[0 to 100%]|
|texture_name =|foreground texture in png format|
|texture2_name =|optional background texture in png format|
|*|fixes the display position of the % set by the button|

## FrontPanel
| front_panel| library \_hmi |
| ------------------------------------------------------|-------|
|latching = |latching front_panel [0,1] [False,True]|
|texture_name =|foreground texture in png format|
|texture2_name =|optional background texture in png format|

## Composition

Adjustable simulation components must be associated with an ihm component.

- Library **_divers_pneumatic** :
![](media/hmi3.png)

- Library **_sensors**
![](media/hmi4.png)

- Library **_resistors**
        - The association of an ihm component is not mandatory for resistor components.

![](media/hmi5.png)