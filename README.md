# PotBot
PotBot c2000 script w rtos

Video of this project here: https://www.youtube.com/watch?v=uYmMaIRG5Y8

Implements RTOS for this 3d printed SCARA robot:

![image](https://user-images.githubusercontent.com/70033294/209588567-66c6836c-4b16-437a-b930-1a8813799362.png)

Files I actually made (as opposed to being generated by Code Composer Studio):
- adc.c/adc.h
- dsp.c/dsp.h
- servo.c/servo.h
- spi.c/spi.h
- uart.c/uart.h
- main.c
- PotBot.cfg

Features of this include:
- Full RTOS on a primary TI C2000 (F28027) with HWIs, SWIs, TSKs, and Idle threading to manage timings of several features
- 3D Scara model built using Solidworks and printed using Cura from scratch
- Takes ADC values from potentiometers for X,Y and FIR N-size
- Uses UART to communicate with a Raspberry Pi to communicate X,Y coordinates of an ArUco marker on a ChArUco board
- A toggle to lower the sharpie to draw with
- Moving average filter to implement FIR
- Inverse kinematics on a fixed point unit to figure out servo joint angles from the current X and Y coordinates
- A toggle to switch between either reading ADC values or Pi Camera values for X and Y coordinates
- Uses SPI to communicate to a secondary C2000 to display X, Y coordinates along with joint coordinates
- Uses the C2000's hardware PWM module to set servo positions for joints 1 and 2, and the linear Z-axis servo
- Reads and conveys temperature through the use of an LED set to a PWM
