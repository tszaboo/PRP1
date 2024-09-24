# User manual

## Introduction
Power rail probes are used to measure the noise, ripple, loop response and other characteristics of power supplies.
These are not standard oscilloscope probes and cannot be used the same way. Proper probing technique is necessary for best performance.
It's recommended to probe the power supplies with regular oscilloscope probe first in 1MOhm mode, and 1:1 or 1:10 attenuation.  
Power rail probes can be used after the general voltage levels have been verified. Their benefits are low intrinsic noise, and low noise pickup due to their construction.
For best noise performance the 50Ohm input path of the oscilloscope is used. The 50Ohm inputs on oscilloscopes have a maximum input voltage rating that's typically 5V. Additionally their DC input resistance is also 50 Ohm. This DC loading often times changes the behaviour of the DUT. For example, a power supply might change from pulse skipping mode to PWM mode after the probe is connected.
Power rail probes provide 50KOhm DC resistance, and 50 Ohm AC impedance, therfore there is minimal loading on the DUT, while the high frequency content of the DUT's noise is also preserved. Power rail probes also limit the DC content to a few hundred millivolts, therefore the 

![image](PRP1-picture.jpg){: width="800px"}

## Safety
Please be advised about these warnings when operating the PRP1
* The ground potential of the PRP1 is the same as the protective Earth potential of the oscilloscope. The PRP1 protective ground shouldn't be connected to other voltage potentials.
* Do not float your oscilloscope Earth potential.
* Use only indoors. No not use in wet environments.
* Do not operate in environments with explosive atmospheres.
* Always make sure the PRP1 is connected to the oscilloscope before connecting to the device under test.
* Do not use the probe if there is any sign of damage to it.
* Do not connect to AC circuits. The probe is only designed to measure DC circuits with small AC component
* Do not use on primary side of mains powered power supply. Only use it on galvanically isolated secondary side

## Connections
![image](PRP1-front.jpg){: width="800px"}

DUT: Connect this to the device under test. Maximum voltage of the connection is 24V. The outer conductor of the SMA connector is referenced to the Earth connection of the oscilloscope and must be connected to the ground connection to the device under test. Ground loops may introduce noise to the system.

Coarse: Potentiometer to adjust the offset voltage. The typical adjustment range of this potentiometer is +24V to -24V.

Fine: Potentiometer to adjust the offset voltage. The typical adjustment range of this potentiometer is +500mV to -500mV.

![image](PRP1-back.jpg){: width="800px"}

USB: Connect this to a 5V powered USB port. The shielding and ground of the USB port is shared with the oscilloscope and shouldn't be connected to other voltages. I recommend powering it with a floating power supply or use the front panel USB port of the oscilloscope.

Power LED: Yellow LED to indicate that the USB is connected and the PRP1 is powered.

Scope: This is the output of the PRP1. Use a SMA to BNC cable to connect it to your oscilloscope.
The maximum DC output voltage of the PRP1 is limited to 2.5V, and with 50 Ohm termination, the typical output range is 500mV.


## Setup
Follow these steps to setup a new measurement with the PRP1
1) Set the input impedance to 50 Ohm on your oscilloscope
2) Connect the USB cable to power the PRP1. The LED should light up
3) Connect the SMA to BNC cable between the Oscilloscope and the PSP1
4) Set your probe attenuation to 1.3:1 to have the correct amplitude reading on your measurements
4) Set your oscilloscope to about 500mV/div to 1V/div input sensitivity
5) Turn the course potentiometer left and right. Verify on the screen that the output voltage of the PRP1 is between 500mV and -500mV
5) Connect the input of the PRP1 to the device under test. See below the best practices for probe selection.
6) Make sure the DUT is powered.
7) Use the course potentiometer on the PRP1 to cancel out the DC component. Reduce the DC component to less than 400mV
8) Increase the input sensitivity of the oscilloscope. Use the fine adjustment on the PRP1 to cancel out the DC component. Repeat this steps if necessary.
9) Your PRP1 is now properly set up. Only steps 8-11 are necessary to repeat when probing subsequent voltage rails

## Probe selection:
Proper probing is essential for best performance of using the PRP1.
The input of the PRP1 should be short, 50Ohm characteristic impedance, and low DC resistance.
Do not use standard oscilloscope probes on the input. They have series resistors in the probe and lossy coax cable. The voltage readings will not be correct.
The following probing methods provide the best performance (highest bandwidth) in most applications:
* Use a SMA to UFL cable for best performance. The DUT could have UFL test points on it to probe the voltage rails
* Use an SMA to pigtail adapter, and solder-in the SMA cable to the DUT. The pigtail could be soldered for example on top of an SMD capacitor close to any high-speed digital device.
* SMA to 2.54mm (0.1") pin header is provided
* An SMA browser can be used. Use the ground clip/header.

## Source impedance
Do not place a resistor series with the probe. The high-speed gain will be reduced, according to the following:

![image](Source-impedance.jpg){: width="800px"}

Do not use standard oscilloscope probes with the PRP1.

## Circuit Loading
The PRP1 has 50 KOhm DC resistance, and 50 Ohm AC impedance.
The input impedance is simulated with the following curve:

![image](Input-impedance.png){: width="800px"}

The equivalent circuit of the probe is the following:

![image](Impedance.png){: width="800px"}

As you can see oscilloscopes with 50 Ohm path provide the best performance. The 50 Ohm BNC termination resistors used with 1MOhm oscilloscopes will limit the bandwidth of the PRP1 probe, depending on their quality. My estimated bandwidth with the popular and cheap P57 termination resistors is about 200MHz.

The capacitive loading of the PRP1 is estimated as 0.5pF, based on the system bandwidth.

It's important that the PRP1 only provides 50 KOhm loading, if it's properly zero’s out on the oscilloscope. Without zeroing out it will inject a small current into the DUT. The voltage it can generate is limited to about 1V, and the source impedance of this current is 50 KOhm. For voltage sensitive circuits this should be considered before connecting the PRP1.
