# EN21478710_Group-15_lab-4
Group 15

![image](https://user-images.githubusercontent.com/111555228/185635559-53d9ddd4-e50e-4dd3-8bf9-a83e2bcc002f.png)
![image](https://user-images.githubusercontent.com/111555228/185639455-38719dc9-5a9b-4668-a131-bb21ff312120.png)



<u> Group 15 </u>
<br>Gamage M.M. - EN21478710
<br>Vindipa K.G.V. - EN21481130
<br>Rathnayake R.M.I.A. - EN21493560



## ABSTRACT


The PIC16f877A microcontroller was mainly used to develop a system for controlling the water level in a water tank. The MPLabs software was used to develop a C language program. Proteus software was used to create a schematic layout of the necessary circuit, which was later converted to a PCB layout to create the circuit that was required. Additionally, DC motors, IR sensors, Motor relays etc. were used to create the required circuit.



## OBJECTIVES

<br>•	To develop a small water level controlling system of a water tank using the knowledge of interrupts and other programming techniques of PIC16f877a.
<br>•	To make suitable code and verify its accuracy using MP LAB
<br>•	To make circuit in the PCB and verify its working procedure
<br>
<br>

## APPARATUS

<br>•  Designed PCB Layout
<br>•  Pic16F877A - 1
<br>•  Breadboard - 1
<br>•  DC Batteries(9V) - 1
<br>•  1k Resistor - 1
<br>•  IR obstacle Avoidance Sensors - 3
<br>•  40 Pin IC Base - 1
<br>•  20Mhz Crystal Oscillator - 1
<br>•  220uf Electrolytic Capacitor - 1
<br>•  LED bulbs - 2
<br>•  Jumper Wires
<br>•  PicKit3
<br>•  MPLAB IDE Software


## INTRODUCTION

<p>One of the most widely used microcontrollers is the PIC16F877A. It has a total of 40 pins, 33 of which are used for input and output. This microcontroller is frequently used in digital electronic circuits and microcontroller projects. This microcontroller's ability to write-erase as many times as possible is one of its key advantages because it has a Flash program memory. Here, the logics are controlled by the microcontroller via input/output to and from external stimuli, respectively.
<br>
An electrical device known as a direct current motor transforms electrical energy into mechanical energy. Direct current is used to generate a magnetic field, which is then converted. Comparing DC motors to other types of motors, the main benefit of using them is the ability to precisely control speed. A sensor is a device that measures a physical input and converts its data so that both machines and humans can read it. IR sensors were used in this experiment.</p>

## Methodology

There is a water tank with two DC motors that are used to pump water into the tank and suction water out of the tank. Three sensors are also used to monitor the water level in the tank. Tank system consists with 1 input motor to pump water in when processing and another motor which expels water from the tank. The first 2 levels are filled with the input motor uninterruptedly, when the input motor starts pumping water above the level of sensor in the 3rd level, the input of that sensor will trigger the output motor to expel water for a duration of 500ms and stop and halt the input motor, simultaneously. 

![image](https://user-images.githubusercontent.com/111555228/185639095-a5890f6b-1e25-4d34-ac7f-e3de0ac7118d.png)

The following table shows how the two DC motors operate in relation to the switch state.

![image](https://user-images.githubusercontent.com/111555228/185639184-e00a6c9d-d0bd-4ba9-ac2a-dce7b524bc4c.png)

A water level indicator is a device that transmits data to a control panel to show whether the water level in a body of water is high or low. A water level indicator's job is to monitor and control the water levels in a tank. It is also possible to program the control panel to activate a water pump automatically when the water level drops below a safe level.

## Simulation and Implementation

### Schematic simulation

![image](https://user-images.githubusercontent.com/111555228/185640272-cacc507d-c115-4bc0-a5b5-cc84c218d96c.png)

With the help of Proteus 8 Professional, (a program that enables users to create PCB designs for the PIC family of microcontrollers and schematic layouts for a wide variety of circuit designs) the designs for the controller were created. It is a perfect computer-based tool because it also supports in-system simulation.

### PCB layout

<img src = "https://user-images.githubusercontent.com/111555228/185640411-31e4d307-662e-4210-8a58-f6937e8eef7f.png" width = 500>
<img src = "https://user-images.githubusercontent.com/111555228/185640668-5469e43e-8cd0-457b-892c-cd43d785ccaa.png" width = 500>


### Image of Real implementation

<img src = "https://user-images.githubusercontent.com/111555228/185640920-efa1cc2f-86b9-498b-9e26-0f0275039b58.png" width = 500>

Here, the PCB acts as the main component. Resistors, PIC16f877A IC, Capacitors, crystal oscillator etc. are included in the PCB. In addition, motor relays, motors and three IR sensors are connected externally through jumper cables.


## CODE

    // PIC16F877A Configuration Bit Settings

    // 'C' source line config statements

    // CONFIG
    #pragma config FOSC = HS        // Oscillator Selection bits (HS oscillator)
    #pragma config WDTE = OFF       // Watchdog Timer Enable bit (WDT disabled)
    #pragma config PWRTE = OFF      // Power-up Timer Enable bit (PWRT disabled)
    #pragma config BOREN = OFF      // Brown-out Reset Enable bit (BOR disabled)
    #pragma config LVP = OFF        // Low-Voltage (Single-Supply) In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for programming)
    #pragma config CPD = OFF        // Data EEPROM Memory Code Protection bit (Data EEPROM code protection off)
    #pragma config WRT = OFF        // Flash Program Memory Write Enable bits (Write protection off; all program memory may be written to by EECON control)
    #pragma config CP = OFF         // Flash Program Memory Code Protection bit (Code protection off)

    // #pragma config statements should precede project file includes.
    // Use project enums instead of #define for ON and OFF.

    //#include <xc.h>
    #include<htc.h> 

    #define _XTAL_FREQ 20000000

    void __interrupt () isr(void) 
{
    if (RB2 == 1 && RB1 == 1)
    {   
        RC0 = 0;
        RC1 = 1;
        __delay_ms(500);
        RC1 = 0;        
    }
    INTF = 0;
    
}
    

