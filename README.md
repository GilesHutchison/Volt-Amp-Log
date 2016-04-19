# Volt-Amp-Log
Raspberry Pi Voltage and Current Data logger for Simprints Fingerprint Scanner

<b>Introduction</b>

Measuring Voltages and Currents is  necessary for some of the manufacturing tests for the Simprints finger print scanners.

One way to do this is to use a Rasbery Pi with an I2C A to D expansion board(s).

<b>Measure Current</b>

If you can measure voltage, you can also measure current using the following method:

Use a high wattage / very low impedance resistor and an Op-Amp you can measure current by amplifying the very small voltage drop across the resistor.

<b>SOFTWARE</b>

1. Download the latest version of Raspian from here
https://www.raspberrypi.org/downloads/

2. Burn onto SD card

3. Configure WiFi to work with SimPrints Access points, by  editing
/etc/network/interfaces
/etc/wpa_supplicant/wpa_supplicant.conf

4. Follow the instructions  on how to configure the Ra Pi A to D
https://www.abelectronics.co.uk/p/17/ADC-Pi-V2---Raspberry-Pi-Analogue-to-Digital-converter

5. Write Python script to repeatedly read and display results, and LOG the results.
Evaluate how often results should be logged to provide usefull information.
save the data as CSV file?

6. Create a Pass Fail result in a python script, depending on current measured, using a threshold read from a text file.

7. Manage data logger file size / culling / management w.r.t. SD card size.

8. Create an additional interface that uses a resfull API to write the I and V measurement information out to a database in the cloud.

<b>HARDWARE</b>

A. Use 2 resistors to make potential dividers to generate voltages to read on A/D channels. 
(Giles)

B. Design a 4 channel  Amplifier using a quad op-amp to amplifiy the voltage across a low R reesistor (that drops 0.1 V at 1Amp) Make sure the resistor is high wattage. Make sure the Vos of the Amplifier is small enough not to cause any issues, or arange to trim it out.

C. Breadboard the circuit, then use an Ameter to check that the current going from the Battery on an Simprints Fingerprint Scanner can be measured as well as the battery voltage.

D. In a standard enclosure, build/ solder a "2 Voltages"  +  "2 Current"  channel data logger.

These channels will be used to measure
i)  3V3 power line
ii) 5V0 power line
iii) Current from Battery
iV) Current from USB 5V input into scanner.

If we need more channels, we can add a second A to D board (on a different I2C ID)

Document design and operation

-END-
