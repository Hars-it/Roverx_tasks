
Arduino UNO

![[Pasted image 20240426233804.png]]

COMPONENTS IN ARDUINO UNO

1) ATmega328 microcontroller IC: 
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

![[Pasted image 20240427110942.png]]


The AVR core combines a rich instruction set with 32 general purpose working registers. All the 32 registers are directly connected to the Arithmetic Logic Unit (ALU), allowing two independent registers to be accessed in one single instruction executed in one clock cycle. The resulting architecture is more code efficient while achieving throughputs up to ten times faster than conventional CISC microcontrollers

The ATmega48A/PA/88A/PA/168A/PA/328/P provides the following features: 4K/8Kbytes of In-System Programmable Flash with Read-While-Write capabilities, 256/512/512/1Kbytes EEPROM, 512/1K/1K/2Kbytes SRAM, 23 general purpose I/O lines, 32 general purpose working registers, three flexible Timer/Counters with compare modes, internal and external interrupts, a serial programmable USART, a byte-oriented 2-wire Serial Interface, an SPI serial port, a 6-channel 10-bit ADC (8 channels in TQFP and QFN/MLF packages), a programmable Watchdog Timer with internal Oscillator, and five software selectable power saving modes. The Idle mode stops the CPU while allowing the SRAM, Timer/Counters, USART, 2-wire Serial Interface, SPI port, and interrupt system to continue functioning. The Power-down mode saves the register contents but freezes the Oscillator, disabling all other chip functions until the next interrupt or hardware reset. In Power-save mode, the asynchronous timer continues to run, allowing the user to maintain a timer base while the rest of the device is sleeping. The ADC Noise Reduction mode stops the CPU and all I/O modules except asynchronous timer and ADC, to minimize switching noise during ADC conversions. In Standby mode, the crystal/resonator Oscillator is running while the rest of the device is sleeping. This allows very fast start-up combined with low power consumption.
support a real Read-While-Write Self-Programming mechanism. There is a separate Boot Loader Section, and the SPM instruction can only execute from there.

CRYSTAL OSCILLATOR
A crystal oscillator is an electronic oscillator circuit that uses a piezoelectric crystal as a frequency-selective element. A crystal oscillator relies on the slight change in shape of a quartz crystal under an electric field, a property known as inverse piezoelectricity. A voltage applied to the electrodes on the crystal causes it to change shape; when the voltage is removed, the crystal generates a small voltage as it elastically returns to its original shape. The quartz oscillates at a stable resonant frequency, behaving like an RLC circuit, but with a much higher Q factor (less energy loss on each cycle of oscillation). Once a quartz crystal is adjusted to a particular frequency (which is affected by the mass of electrodes attached to the crystal, the orientation of the crystal, temperature and other factors), it maintains that frequency with high stability.
The Arduino uses a crystal frequency of 16Mhz.

DC CONNECTOR
A DC connector is an electrical connector for supplying direct current power. The intended use of these plugs is on the cable connected to an external AC adapter (power supply). The matching jack or socket is permanently fitted to the equipment to be powered. Some of these jacks contain a normally closed contact, which can be used to disconnect internal batteries whenever the power supply is connected, avoiding the risk of battery leakage or explosion posed by incorrect recharging of the batteries.

ICSP
 In-circuit serial programming (ICSP), is the ability of some programmable logic devices, microcontrollers, chipsets and other embedded devices to be programmed while installed in a complete system, rather than requiring the chip to be programmed prior to installing it into the system. It also allows firmware updates to be delivered to the on-chip memory of microcontrollers and related processors without requiring specialist programming circuitry on the circuit board, and simplifies design work.

Arduino Architecture
Arduino’s processor basically uses the Harvard architecture where the program code and program data have separate memory. It consists of two memories- Program memory and the data memory.The code is stored in the flash program memory, whereas the data is stored in the data memory. The Atmega328 has 32 KB of flash memory for storing code (of which 0.5 KB is used for the bootloader), 2 KB of SRAM and 1 KB of EEPROM and operates with a clock speed of 16MHz.
![Arduino Architecture](https://www.elprocus.com/wp-content/uploads/2013/08/2.jpg)
Arduino Uno consists of 14 digital input/output pins (of which 6 can be used as PWM outputs), 6 analog inputs, a 16 MHz crystal oscillator, a USB connection, a power jack, an ICSP header, and a reset button

Power Jack:  Arduino can be power either from the pc through a USB or through external source like adaptor or a battery. It can operate on a external supply of 7 to 12V. Power can be applied externally through the pin Vin or by giving voltage reference through the IORef pin.

Digital Inputs: It consists of 14 digital inputs/output pins, each of which provide or take up 40mA current. Some of them have special functions like pins 0 and 1, which act as Rx and Tx respectively , for serial communication, pins 2 and 3-which are external interrupts, pins 3,5,6,9,11 which provides pwm output and pin 13 where LED is connected.

Analog inputs: It has 6 analog input/output pins, each providing a resolution of 10 bits.
ARef: It provides reference to the analog inputs
Reset: It resets the microcontroller when low

INTERRUPT
The interrupt is a signal emitted by hardware or software when a process or an event needs immediate attention. It alerts the processor to a high-priority process requiring interruption of the current working process. In I/O devices one of the bus control lines is dedicated for this purpose and is called the Interrupt Service Routine (ISR). 
When a device raises an interrupt at let’s say process i, the processor first completes the execution of instruction i. Then it loads the Program Counter (PC) with the address of the first instruction of the ISR. Before loading the Program Counter with the address, the address of the interrupted instruction is moved to a temporary location. Therefore, after handling the interrupt the processor can continue with process i+1.
While the processor is handling the interrupts, it must inform the device that its request has been recognized so that it stops sending the interrupt request signal. Also, saving the registers so that the interrupted process can be restored in the future, increases the delay between the time an interrupt is received and the start of the execution of the ISR. This is called Interrupt Latency.

EEPROM
EEPROM is an acronym that stands for Electrically Erasable Programmable Read-Only Memory. It denotes a type of rewritable storage chip or memory package that can continue to hold its stored information even without power. This is known as non-volatile memory.
Electrically erasable
- When connected to a power supply (PSU) via a motherboard or other suitable electronic circuit, the stored contents of EEPROM modules can be erased (deleted), either entirely or on an individual byte-per-section basis
Programable
- ROM, or programmable ROM, indicates a module whose contents are intended to be written to memory after the chip has been installed into a system
- When attached to an appropriate circuit, for example as part of a desktop computer system, the application of electrical voltages to EEPROM chips allows users to modify or reprogram the contents stored on the memory module
Read- only
- Read-only memory (ROM and PROM) refers to modules designed for the long-term storage of information that does not change dynamically
- Non-dynamic data includes most types of user files, firmware, and some programs or code - elements that are not intended to receive regular automatic updates
- Like most ROM chips, EEPROM modules provide non-volatile functionality. This means any information stored on the chip can still be retrieved after a zero-power state, i.e. after the device or computer it is installed in has been turned off and back on again. This is not the case with RAM (Random Access Memory). RAM is designed for performing dynamic tasks rather than long-term information storage and is effectively wiped at the instant it reverts to a powered-off state

ADC
Analogue to Digital Converter, or ADC, is a data converter which allows digital circuits to interface with the real world by encoding an analogue signal into a binary code. An analogue to digital converter takes a snapshot of an analogue voltage at one instant in time and produces a digital output code which represents this analogue voltage. The number of binary digits, or bits used to represent this analogue voltage value depends on the resolution of an A/D converter.  4-bit ADC will have a resolution of one part in 15, (24 – 1) whereas an 8-bit ADC will have a resolution of one part in 255, (28 – 1). Thus an analogue to digital converter takes an unknown continuous analogue signal and converts it into an “n”- bit binary number of 2n bits.

3-bit ADC
![[Screenshot 2024-04-27 222227.png]]




