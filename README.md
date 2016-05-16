# Volt-Amp-Log
Raspberry Pi Voltage and Current Data logger for Simprints Fingerprint Scanner
Hardware Design
---------------
Information about the I2C A to D board

We have two of the following boards

https://www.abelectronics.co.uk/p/17/ADC-Pi-V2---Raspberry-Pi-Analogue-to-Digital-converter

Based on the MCP3424 from Microchip Technologies Inc
http://ww1.microchip.com/downloads/en/DeviceDoc/22088b.pdf

These quad A to D's have an on-Board Voltage Reference (VREF): 2.048V ± 0.05%

#Volts per bit
The A to D boards have a potential divider:
                       _____ Input to A to D
                      |
Input = 10K __/\/\/\__|__ 6K8 __/\/\/\__to AGND

Therefore, 5V in divides down to (5 x 6.8)/16.8 =2.023, which is a very close match for VREF.
at 16 bits, one bit = 5/(256 x 256) = 76uV
at 12 bits, one bit = 5/ (16x256) = 1.2mV

#Measure Current at up to 1 AMP
Assume 1% voltage drop acceptable on Sense resistor
At 5V, this is a potential error of 50mV
At 1 Amp this is a drop of 50mV => Giving a Sense resistor value of R= 0.050/1
Power lost as heat = I^2R = 50mW
NOTE: 0.1R resistors much more common than 0.05 ohm resistors, so use two 0.1mOhm in parrallel.

Potential Farnell part numbers are:

£0.14 each @5% F. MCKNP01SJ010KA10
£2.70 each @1% F. WNCR10FE

n

#OPAMP

http://www.farnell.com/datasheets/1896189.pdf
JFET low input offset voltage 1mV
We want 50mV to give 5V out, amplification of 100
Offset voltage 1mV will amplify to 0.1V at amplification of 100 or 2%

#Power Supplies

power supply of +/-6V's, 5V for Pi or possibly +/-5V using this Farnell part 2079668


Use two dual devices, to provide quad Current ,measurement and quad Voltage measurement on an 8 channel A to D board.


#i2C address

Select the correct Jumper possitions
See
https://www.abelectronics.co.uk/p/56/ADC-Pi-Plus-Raspberry-Pi-Analogue-to-Digital-converter

parts to Buy
DIL 8x2 Pins
Breadboard

Note: single trimpots cost £0.20 e.G. 
PVZ2A104C04R00   100K SM

#RELAYS
http://www.farnell.com/datasheets/1717943.pdf
Contacts 450mW at 5V = 100mA
Contact resistance 100mOhms which is approximately identical to the sense resistor.

#TRANSISTOR

NPN, BC337, 500mA, 650mW, 400hfe, 100MHz, £0.11 each

Software for A to D board

#Python on the Pi
Install Python on the Ra Pi.

git clone the following repositories

https://github.com/abelectronicsuk/ABElectronics_C_Libraries
https://github.com/abelectronicsuk/ABElectronics_Python_Libraries.git
https://github.com/abelectronicsuk/ABElectronics_Python3_Libraries.git

#Software
The RTOS running on the NXP ARM in the Index scanner is FreeRTOS
