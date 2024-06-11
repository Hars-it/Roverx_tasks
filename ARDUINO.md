![[Pasted image 20240426233804.png]]
Pinout
![[Pasted image 20240501070753.png]]
![[Pasted image 20240501070929.png]]
![[Pasted image 20240501071004.png]]
![[Pasted image 20240501071348.png]]
![[Pasted image 20240501071414.png]]

## CAPACITOR##

SMD capacitors are classified into different types based on the dielectric material used like the following.

- Multilayer Ceramic Capacitor
- Tantalum Capacitor
- Electrolytic Capacitor

Multilayer Ceramic Capacitor

In this type of capacitor, ceramic is used as a dielectric material. These capacitors are rated based on the electrical properties of ceramic. So the property of ceramic is multidimensional. The ceramic which is used in the capacitor will reduce the size of the capacitor as compared with other types. In ceramic capacitors, different ceramic dioxides are used such as barium strontium, barium titanate & titanium dioxide, etc.

Tantalum Capacitor

Tantalum capacitors are used widely to give high levels of capacitance compared with ceramic capacitors. Based on the results of the design & requirements of these capacitors, there are some packages are used to design these capacitors. This capacitor has some values which can be identified by marking, respective standards & coding methods

Electrolytic Capacitor

This capacitor is used in SMD designs due to the high level of capacitance and low cost. These capacitors are frequently marked with voltage and its value. In this type, there are two kinds of methods are used.  
The first method is to include µF values whereas another method is to utilize code. In the first method, when the capacitor is marked with 33 and indicated with 6v then the value of the capacitor is 33 µF and the voltage used is 6V.

![[Pasted image 20240501074653.png]]







Arduino Architecture
Arduino’s processor basically uses the Harvard architecture where the program code and program data have separate memory. It consists of two memories- Program memory and the data memory. The code is stored in the flash program memory, whereas the data is stored in the data memory. The Atmega328 has 32 KB of flash memory for storing code (of which 0.5 KB is used for the bootloader), 2 KB of SRAM and 1 KB of EEPROM and operates with a clock speed of 16MHz.
![Arduino Architecture](https://www.elprocus.com/wp-content/uploads/2013/08/2.jpg)
Arduino Uno consists of 14 digital input/output pins (of which 6 can be used as PWM outputs), 6 analog inputs, a 16 MHz crystal oscillator, a USB connection, a power jack, an ICSP header, and a reset button

Power Jack:  Arduino can be power either from the pc through a USB or through external source like adaptor or a battery. It can operate on a external supply of 7 to 12V. Power can be applied externally through the pin Vin or by giving voltage reference through the IORef pin.

Digital Inputs: It consists of 14 digital inputs/output pins, each of which provide or take up 40mA current. Some of them have special functions like pins 0 and 1, which act as Rx and Tx respectively , for serial communication, pins 2 and 3-which are external interrupts, pins 3,5,6,9,11 which provides pwm output and pin 13 where LED is connected.

Analog inputs: It has 6 analog input/output pins, each providing a resolution of 10 bits.
ARef: It provides reference to the analog inputs
Reset: It resets the microcontroller when low


## OSCILLATOR ##
An **oscillator** is a circuit that creates a continuous, alternating waveform from a DC source without any external input. It converts a one-way current into an alternating waveform at a frequency determined by its components.
 CRYSTAL OSCILLATOR
  A crystal oscillator is an electronic oscillator circuit that uses a piezoelectric crystal as a frequency-selective element. A crystal oscillator relies on the slight change in shape of a quartz crystal under an electric field, a property known as inverse piezoelectricity. A voltage applied to the electrodes on the crystal causes it to change shape; when the voltage is removed, the crystal generates a small voltage as it elastically returns to its original shape. The quartz oscillates at a stable resonant frequency, behaving like an RLC circuit, but with a much higher Q factor (less energy loss on each cycle of oscillation). Once a quartz crystal is adjusted to a particular frequency (which is affected by the mass of electrodes attached to the crystal, the orientation of the crystal, temperature and other factors), it maintains that frequency with high stability.
  The Arduino uses a crystal frequency of 16Mhz.

## Arduino Architecture ##
Arduino’s processor basically uses the Harvard architecture where the program code and program data have separate memory. It consists of two memories- Program memory and the data memory. The code is stored in the flash program memory, whereas the data is stored in the data memory. The Atmega328 has 32 KB of flash memory for storing code (of which 0.5 KB is used for the bootloader), 2 KB of SRAM and 1 KB of EEPROM and operates with a clock speed of 16MHz.
![Arduino Architecture](https://www.elprocus.com/wp-content/uploads/2013/08/2.jpg)
Arduino Uno consists of 14 digital input/output pins (of which 6 can be used as PWM outputs), 6 analog inputs, a 16 MHz crystal oscillator, a USB connection, a power jack, an ICSP header, and a reset button

Power Jack:  Arduino can be power either from the pc through a USB or through external source like adaptor or a battery. It can operate on a external supply of 7 to 12V. Power can be applied externally through the pin Vin or by giving voltage reference through the IORef pin.

Digital Inputs: It consists of 14 digital inputs/output pins, each of which provide or take up 40mA current. Some of them have special functions like pins 0 and 1, which act as Rx and Tx respectively , for serial communication, pins 2 and 3-which are external interrupts, pins 3,5,6,9,11 which provides pwm output and pin 13 where LED is connected.

Analog inputs: It has 6 analog input/output pins, each providing a resolution of 10 bits.
ARef: It provides reference to the analog inputs
Reset: It resets the microcontroller when low

## ATmega328 microcontroller IC ##
![[Pasted image 20240427101829.png]]

Pin Descriptions
a) VCC
Digital supply voltage.
b) GND
Ground.
c) Port B (PB7:0) XTAL1/XTAL2/TOSC1/TOSC2
Port B is an 8-bit bi-directional I/O port with internal pull-up resistors (selected for each bit). The Port B output buffers have symmetrical drive characteristics with both high sink and source capability. As inputs, Port B pins that are externally pulled low will source current if the pull-up resistors are activated. The Port B pins are tri-stated when a reset condition becomes active, even if the clock is not running. Depending on the clock selection fuse settings, PB6 can be used as input to the inverting Oscillator amplifier and input to the internal clock operating circuit. Depending on the clock selection fuse settings, PB7 can be used as output from the inverting Oscillator amplifier.
If the Internal Calibrated RC Oscillator is used as chip clock source, PB7...6 is used as TOSC2...1 input for the Asynchronous Timer/Counter2 if the AS2 bit in ASSR is set.
c) Port C (PC5:0)
Port C is a 7-bit bi-directional I/O port with internal pull-up resistors (selected for each bit). The PC5...0 output buffers have symmetrical drive characteristics with both high sink and source capability. As inputs, Port C pins that are externally pulled low will source current if the pull-up resistors are activated. The Port C pins are tri-stated when a reset condition becomes active, even if the clock is not running.
d) PC6/RESET
If the RSTDISBL Fuse is programmed, PC6 is used as an I/O pin. Note that the electrical characteristics of PC6 differ from those of the other pins of Port C.
If the RSTDISBL Fuse is unprogrammed, PC6 is used as a Reset input. A low level on this pin for longer than the minimum pulse length will generate a Reset, even if the clock is not running.  Shorter pulses are not guaranteed to generate a Reset.
d) Port D (PD7:0)
Port D is an 8-bit bi-directional I/O port with internal pull-up resistors (selected for each bit). The Port D output buffers have symmetrical drive characteristics with both high sink and source capability. As inputs, Port D pins that are externally pulled low will source current if the pull-up resistors are activated. The Port D pins are tri-stated when a reset condition becomes active, even if the clock is not running.
e) AVCC
AVCC is the supply voltage pin for the A/D Converter, PC3:0, and ADC7:6. It should be externally connected to VCC, even if the ADC is not used. If the ADC is used, it should be connected to VCC through a low-pass filter. PC6...4 use digital supply voltage, VCC.
f) AREF
AREF is the analog reference pin for the A/D Converter.
g) ADC7:6 (TQFP and QFN/MLF Package Only)
In the TQFP and QFN/MLF package, ADC7:6 serve as analog inputs to the A/D converter. These pins are powered from the analog supply and serve as 10-bit ADC channels.

![[Pasted image 20240501092639.png]]
![[Pasted image 20240501092715.png]]
![[Pasted image 20240501092812.png]]


## ADC
Analog to Digital Converter, or ADC, is a data converter which allows digital circuits to interface with the real world by encoding an analogue signal into a binary code. An analogue to digital converter takes a snapshot of an analogue voltage at one instant in time and produces a digital output code which represents this analogue voltage. The number of binary digits, or bits used to represent this analogue voltage value depends on the resolution of an A/D converter.  4-bit ADC will have a resolution of one part in 15, (24 – 1) whereas an 8-bit ADC will have a resolution of one part in 255, (28 – 1). Thus an analogue to digital converter takes an unknown continuous analogue signal and converts it into an “n”- bit binary number of 2n bits.

3-bit ADC
![[Screenshot 2024-04-27 222227.png]]
![[Pasted image 20240501093927.png]]
![[Pasted image 20240501093956.png]]
![[Pasted image 20240501094026.png]]





## ICSP##
 In-circuit serial programming (ICSP), is the ability of some programmable logic devices, microcontrollers, chipsets and other embedded devices to be programmed while installed in a complete system, rather than requiring the chip to be programmed prior to installing it into the system. It also allows firmware updates to be delivered to the on-chip memory of microcontrollers and related processors without requiring specialist programming circuitry on the circuit board, and simplifies design work.
 ![[Pasted image 20240526102900.png]]


 