**STM32** is a family of 32-bit microcontroller integrated circuits by STMicroelectronics. The STM32 chips are grouped into related series that are based around the same [32-bit](https://en.wikipedia.org/wiki/32-bit "32-bit") [ARM](https://en.wikipedia.org/wiki/ARM_architecture "ARM architecture") processor core: [Cortex-M0](https://en.wikipedia.org/wiki/ARM_Cortex-M0 "ARM Cortex-M0"), [Cortex-M0+](https://en.wikipedia.org/wiki/ARM_Cortex-M0%2B "ARM Cortex-M0+"), [Cortex-M3](https://en.wikipedia.org/wiki/ARM_Cortex-M3 "ARM Cortex-M3"), [Cortex-M4](https://en.wikipedia.org/wiki/ARM_Cortex-M4 "ARM Cortex-M4"), [Cortex-M7](https://en.wikipedia.org/wiki/ARM_Cortex-M#Cortex-M7 "ARM Cortex-M"), [Cortex-M33](https://en.wikipedia.org/wiki/ARM_Cortex-M#Cortex-M33 "ARM Cortex-M"). Internally, each microcontroller consists of ARM processor core(s), [flash memory](https://en.wikipedia.org/wiki/Flash_memory "Flash memory"), [static RAM](https://en.wikipedia.org/wiki/Static_RAM "Static RAM"), debugging interface, and various peripherals.
![[Screenshot 2024-06-03 194743.png]]
### STM32 F0
The STM32 F0-series are the first group of ARM Cortex-M0 chips in the STM32 family.
- Core:
	- ARM Cortex-M0 core at a maximum clock rate of 48 MHz.
	- Cortex-M0 options include the SysTick Timer.
- Memory:
	- Static RAM consists of 4 / 6 / 8 / 16 / 32 KB general purpose with hardware parity checking.
	- Flash consists of 16 / 32 / 64 / 128 / 256 KB general purpose.
	- Each chip has a factory-programmed 96-bit unique device identifier number. (except STM32F030x4/6/8/C and STM32F070x6/B)
- Peripherals:
	- Each F0-series includes various peripherals that vary from line to line.
	- Oscillators consists of internal (8 MHz, 40 kHz), optional external (1 to 32 MHz, 32.768 to 1000 kHz).
IC packages: TSSOP20, UFQFPN32, LQFP/UFQFN48, LQFP64, LQFP/UFBGA100.
Operating voltage range is 2.0 to 3.6 volt with the possibility to go down to 1.65 V.

### STM32 F1
The STM32 F1-series was the first group of STM32 microcontrollers based on the ARM Cortex-M3 core and considered their mainstream ARM microcontrollers. The F1-series has evolved over time by increasing CPU speed, size of internal memory, variety of peripherals. There are five F1 lines: Connectivity (STM32F105/107), Performance (STM32F103), USB Access (STM32F102), Access (STM32F101), Value (STM32F100). 

- Core:
	- ARM Cortex-M3 core at a maximum clock rate of 24 / 36 / 48 / 72 MHz.
- Memory:
	- Static RAM consists of 4 / 6 / 8 / 10 / 16 / 20 / 24 / 32 / 48 / 64 / 80 / 96 KB.
	- Flash consists of 16 / 32 / 64 / 128 / 256 / 384 / 512 / 768 / 1024 KB.
- Peripherals:
	- Each F1-series includes various peripherals that vary from line to line.
- IC packages: VFQFPN36, VFQFPN48, LQFP48, WLCSP64, TFBGA64, LQFP64, LQFP100, LFBGA100, LQFP144, LFBGA144.

### STM32 F2
The STM32 F2 series is a family of microcontrollers from STMicroelectronics that are based on the ARM Cortex-M3 core. These microcontrollers are designed for applications that require a high-performance core along with a variety of integrated features.

- Core:
	- ARM Cortex-M3 core at a maximum clock rate of 120 MHz.
- Memory:
	- Static RAM consists of 64 / 96 / 128 KB general purpose, 4 KB battery-backed, 80 bytes battery-backed with tamper-detection erase.
	- Flash consists of 128 / 256 / 512 / 768 / 1024 KB general purpose, 30 KB system boot, 512 bytes one-time programmable (OTP), 16 option bytes.
	- Each chip has a factory-programmed 96-bit unique device identifier number.
- Peripherals:
	- Common peripherals included in all IC packages are USB 2.0 OTG HS, two CAN 2.0B, one SPI + two SPI or I²S, three I²C, four USART, two UART, SDIO/MMC, twelve 16-bit timers, two 32-bit timers, two watchdog timers, temperature sensor, 16 or 24 channels into three ADCs, two DACs, 51 to 140 GPIOs, sixteen DMA, real-time clock (RTC), cyclic redundancy check (CRC) engine, random number generator (RNG) engine. Larger IC packages add 8/16-bit external memory bus capabilities.
	- The STM32F2x7 models add Ethernet MAC, camera interface, USB 2.0 OTG FS.
	- The STM32F21x models add a cryptographic processor for DES / TDES / AES, and a hash processor for SHA-1 and MD5.
- Oscillators consists of internal (16 MHz, 32 kHz), optional external (4 to 26 MHz, 32.768 to 1000 kHz).
- IC packages: WLCSP64, LQFP64, LQFP100, LQFP144, LQFP176, UFBGA176.
- Operating voltage range is 1.8 to 3.6 volt.
### Applications
The STM32 F2 series is suited for a wide range of applications, including:
- Industrial control and automation
- Consumer electronics
- Medical devices
- Communication and networking equipment
- Motor control and power management
- Security and surveillance systems

### STM32 F3
The STM32 F3-series is the second group of STM32 microcontrollers based on the ARM Cortex-M4F core. The F3 is almost pin-to-pin compatible with the STM32 F1-series.

- Core:
    - [ARM Cortex-M4F](https://en.wikipedia.org/wiki/ARM_Cortex-M4F "ARM Cortex-M4F") core at a maximum clock rate of 72 [MHz](https://en.wikipedia.org/wiki/MHz "MHz").
- Memory:
    - [Static RAM](https://en.wikipedia.org/wiki/Static_RAM "Static RAM") consists of 16 / 24 / 32 / 40 KB general purpose with hardware parity check, 0 / 8 KB core coupled memory (CCM) with hardware parity check, 64 / 128 bytes battery-backed with tamper-detection erase.
    - Flash consists of 64 / 128 / 256 [KB](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") general purpose, 8 [KB](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") system boot, and option bytes.
    - Each chip has a factory-programmed 96-bit unique device identifier number.
- Peripherals:
    - Each F3-series includes various peripherals that vary from line to line.
- [Oscillators](https://en.wikipedia.org/wiki/Electronic_oscillator "Electronic oscillator") consists of internal (8 MHz, 40 kHz), optional external (1 to 32 MHz, 32.768 to 1000 kHz).
- [IC packages](https://en.wikipedia.org/wiki/Integrated_circuit_packaging "Integrated circuit packaging"): [LQFP](https://en.wikipedia.org/wiki/LQFP "LQFP")48, LQFP64, LQFP100, [UFBGA](https://en.wikipedia.org/wiki/UFBGA "UFBGA")100.
- Operating [voltage](https://en.wikipedia.org/wiki/IC_power_supply_pin "IC power supply pin") range is 2.0 to 3.6 [volt](https://en.wikipedia.org/wiki/Volt "Volt").

The distinguishing feature for this series is presence of four fast, 12-bit, simultaneous sampling ADCs (multiplexer to over 30 channels), and four matched, 8 MHz bandwidth op-amps with all pins exposed and additionally internal PGA (Programmable Gain Array) network. The exposed pads allow for a range of analog signal conditioning circuits like band-pass filters, anti-alias filters, charge amplifiers, integrators/differentiators, 'instrumentation' high-gain differential inputs, and other. This eliminates need for external op-amps for many applications. The built-in two-channel DAC has arbitrary waveform as well as a hardware-generated waveform (sine, triangle, noise etc.) capability. All analog devices can be completely independent, or partially internally connected, meaning that one can have nearly everything that is needed for an advanced measurement and sensor interfacing system in a single chip.

The four ADCs can be simultaneously sampled making a wide range of precision analog control equipment possible. It is also possible to use a hardware scheduler for the multiplexer array, allowing good timing accuracy when sampling more than 4 channels, independent of the main processor thread. The sampling and multiplexing trigger can be controlled from a variety of sources including timers and built-in comparators, allowing for irregular sampling intervals where needed.

STM32F37/38xxx integrate a 14-effective number of bits delta-sigma ADC.

The op-amps inputs feature 2-to-1 analog multiplexer, allowing for a total of eight analog channels to be pre-processed using the op-amp; all the op-amp outputs can be internally connected to ADCs.
### Applications

The STM32 F3 series is ideal for a wide range of applications, including:

- Digital power supplies
- Motor control
- Medical devices
- Industrial control and automation
- Consumer electronics
- Audio processing
- Home appliances

### STM32 F4
The STM32 F4-series is the first group of STM32 microcontrollers based on the ARM Cortex-M4F core. The F4-series is also the first STM32 series to have DSP and floating-point instructions. The F4 is [pin-to-pin compatible](https://en.wikipedia.org/wiki/Pin-compatibility "Pin-compatibility") with the STM32 F2-series and adds higher clock speed, 64 KB CCM static RAM, full-duplex I²S, improved real-time clock, and faster ADCs.

- Core:
    - [ARM Cortex-M4F](https://en.wikipedia.org/wiki/ARM_Cortex-M4F "ARM Cortex-M4F") core at a maximum clock rate of 84 / 100 / 168 / 180 [MHz](https://en.wikipedia.org/wiki/MHz "MHz").
- Memory:
    - [Static RAM](https://en.wikipedia.org/wiki/Static_RAM "Static RAM") consists of up to 192 KB general-purpose, 64 KB core-coupled memory (CCM), 4 KB battery-backed, 80 bytes battery-backed with tamper-detection erase.
    - Flash consists of 512 / 1024 / 2048 [KB](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") general-purpose, 30 KB system boot, 512 bytes one-time programmable (OTP), 16 option bytes.
    - Each chip has a factory-programmed 96-bit unique device identifier number.
- Peripherals:
    - Common peripherals included in all IC packages are [USB](https://en.wikipedia.org/wiki/USB "USB") 2.0 [OTG](https://en.wikipedia.org/wiki/USB_On-The-Go "USB On-The-Go") HS and FS, two [CAN](https://en.wikipedia.org/wiki/Controller_area_network "Controller area network") 2.0B, one [SPI](https://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus "Serial Peripheral Interface Bus") + two SPI or full-duplex [I²S](https://en.wikipedia.org/wiki/I%C2%B2S "I²S"), three [I²C](https://en.wikipedia.org/wiki/I%C2%B2C "I²C"), four [USART](https://en.wikipedia.org/wiki/USART "USART"), two [UART](https://en.wikipedia.org/wiki/UART "UART"), [SDIO](https://en.wikipedia.org/wiki/Secure_Digital#SDIO "Secure Digital") for [SD](https://en.wikipedia.org/wiki/Secure_Digital "Secure Digital")/[MMC](https://en.wikipedia.org/wiki/MultiMediaCard "MultiMediaCard") cards, twelve 16-bit [timers](https://en.wikipedia.org/wiki/Timers#Computer_timers "Timers"), two 32-bit timers, two [watchdog](https://en.wikipedia.org/wiki/Watchdog_timer "Watchdog timer") timers, [temperature](https://en.wikipedia.org/wiki/Temperature "Temperature") sensor, 16 or 24 channels into three [ADCs](https://en.wikipedia.org/wiki/Analog-to-digital_converter "Analog-to-digital converter"), two [DACs](https://en.wikipedia.org/wiki/Digital-to-analog_converter "Digital-to-analog converter"), 51 to 140 [GPIOs](https://en.wikipedia.org/wiki/General-purpose_input/output "General-purpose input/output"), sixteen [DMA](https://en.wikipedia.org/wiki/Direct_memory_access "Direct memory access"), improved real-time clock ([RTC](https://en.wikipedia.org/wiki/Real-time_clock "Real-time clock")), [cyclic redundancy check](https://en.wikipedia.org/wiki/Cyclic_redundancy_check "Cyclic redundancy check") (CRC) engine, [random number generator](https://en.wikipedia.org/wiki/Random_number_generation "Random number generation") (RNG) engine. Larger IC packages add 8/16-bit external [memory bus](https://en.wikipedia.org/wiki/Memory_bus "Memory bus") capabilities.
        - Digital filter for sigma-delta modulators (DFSDM) interface in STM32F412 and STM32F413/423 lines[[30]](https://en.wikipedia.org/wiki/STM32#cite_note-:0-30)
    - The STM32F4x7 models add [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet") [MAC](https://en.wikipedia.org/wiki/Media_Independent_Interface "Media Independent Interface") and [camera interface](https://en.wikipedia.org/wiki/Camera_interface "Camera interface").
    - The STM32F41x/43x models add a [cryptographic processor](https://en.wikipedia.org/wiki/Cryptographic_accelerator "Cryptographic accelerator") for [DES](https://en.wikipedia.org/wiki/Data_Encryption_Standard "Data Encryption Standard") / [TDES](https://en.wikipedia.org/wiki/Triple_DES "Triple DES") / [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard "Advanced Encryption Standard"), and a hash processor for [SHA-1](https://en.wikipedia.org/wiki/SHA-1 "SHA-1") and [MD5](https://en.wikipedia.org/wiki/MD5 "MD5").
    - The STM32F4x9 models add a [LCD-TFT](https://en.wikipedia.org/wiki/TFT_LCD "TFT LCD") controller.
- [Oscillators](https://en.wikipedia.org/wiki/Electronic_oscillator "Electronic oscillator") consists of internal (16 MHz, 32 kHz), optional external (4 to 26 MHz, 32.768 to 1000 kHz).
- [IC packages](https://en.wikipedia.org/wiki/Integrated_circuit_packaging "Integrated circuit packaging"): [WLCSP](https://en.wikipedia.org/wiki/WLCSP "WLCSP")64, [LQFP](https://en.wikipedia.org/wiki/LQFP "LQFP")64, LQFP100, LQFP144, LQFP176, [UFBGA](https://en.wikipedia.org/wiki/UFBGA "UFBGA")176. STM32F429/439 also offers LQFP208 and [UFBGA](https://en.wikipedia.org/wiki/UFBGA "UFBGA")216.
- Operating [voltage](https://en.wikipedia.org/wiki/IC_power_supply_pin "IC power supply pin") range is 1.8 to 3.6 [volt](https://en.wikipedia.org/wiki/Volt "Volt").

Application
The STM32 F4 series is well-suited for applications that require high performance, rich connectivity, and advanced peripherals, including:

- Industrial automation and control
- Consumer electronics
- Audio and multimedia
- Communication and networking equipment
- Medical devices
- Motor control and power management

### STM32 G0
The STM32 G0-series is a next generation of Cortex-M0/M0+ microcontrollers for budget market segment, offering the golden mean in productivity and power efficiency, e.g. better power efficiency and performance compared to the older F0 series and higher performance compared to ultra low power L0 series.

- Core:
    - [ARM Cortex-M0+](https://en.wikipedia.org/wiki/ARM_Cortex-M0%2B "ARM Cortex-M0+") core at a maximum clock rate of 64 MHz.
    - Debug interface is [SWD](https://en.wikipedia.org/wiki/Serial_Wire_Debug "Serial Wire Debug") with breakpoints and watchpoints. [JTAG](https://en.wikipedia.org/wiki/JTAG "JTAG") debugging isn't supported.
- Memory:
    - Static RAM sizes of 8 to 128 KB general purpose with hardware parity checking and up to 144 KB without hardware parity checking, 5x 32-bit battery-backed registers with tamper-detection erase.
    - Flash sizes of 16 to 512 KB.

### STM32 G4
The STM32 G4-series is a next generation of Cortex-M4F microcontrollers aiming to replace F3 series, offering the golden mean in productivity and power efficiency, e.g. better power efficiency and performance compared to the older F3/F4 series and higher performance compared to ultra low power L4 series, integrated several hardware accelerators.

- Core:
    - [ARM Cortex-M4F](https://en.wikipedia.org/wiki/ARM_Cortex-M4F "ARM Cortex-M4F") core at a maximum clock rate of 170 MHz with FPU and DSP instructions
- Mathematical accelerators:
    - CORDIC (trigonometric and hyperbolic functions)
    - FMAC (filtering functions)
- Memory:
    - Flash memory with error-correcting code (ECC) and sizes of 128 to 512 KB.
    - [Static RAM](https://en.wikipedia.org/wiki/Static_RAM "Static RAM") sizes of 32 to 128 KB with hardware parity checking and CCM-SRAM routine booster, 32x 32-bit battery-backed registers with tamper-detection erase.
- Rich advanced analog peripherals (comparator, op-amps, DAC)
- ADC with hardware oversampling (16-bit resolution) up to 4 Msps
- High-resolution timer version 2
- USB Type-C interface with Power Delivery including physical layer (PHY)
- Securable memory area
- AES hardware encryption

### STM32 H7
The STM32 H7-series is a group of high performance STM32 microcontrollers based on the ARM Cortex-M7F core with double-precision floating point unit and optional second Cortex-M4F core with single-precision floating point. Cortex-M7F core can reach working frequency up to 480 MHz, while Cortex-M4F - up to 240 MHz. Each of these cores can work independently or as master/slave core.

The STM32H7 Series is the first series of STM32 microcontrollers in 40 nm process technology and the first series of ARM Cortex-M7-based microcontrollers which is able to run up to 480 MHz, allowing a performance boost versus previous series of Cortex-M microcontrollers, reaching new performance records of 1027 DMIPS and 2400 CoreMark. 

Digital filter for sigma-delta modulators (DFSDM) interface.

### STM32 L0
The STM32 L0-series is the first group of STM32 microcontrollers based on the ARM Cortex-M0+ core. This series targets low power applications.

- Core:
    - [ARM Cortex-M0+](https://en.wikipedia.org/wiki/ARM_Cortex-M0%2B "ARM Cortex-M0+") core at a maximum clock rate of 32 [MHz](https://en.wikipedia.org/wiki/MHz "MHz").
    - Debug interface is [SWD](https://en.wikipedia.org/wiki/Serial_Wire_Debug "Serial Wire Debug") with breakpoints and watchpoints. JTAG debugging isn't supported.
- Memory:
    - [Static RAM](https://en.wikipedia.org/wiki/Static_RAM "Static RAM") sizes of 8 [KB](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") general purpose with hardware parity checking, 20 bytes battery-backed with tamper-detection erase.
    - Flash sizes of 32 or 64 KB general purpose (with ECC).
    - [EEPROM](https://en.wikipedia.org/wiki/EEPROM "EEPROM") sizes of 2 KB (with ECC).
    - [ROM](https://en.wikipedia.org/wiki/Read-only_memory "Read-only memory") which contains a boot loader with optional reprogramming of the flash from USART1, USART2, SPI1, SPI2.
    - Each chip has a factory-programmed 96-bit unique device identifier number.
- Peripherals:
    - two [USART](https://en.wikipedia.org/wiki/USART "USART"), one low-power UART, two [I²C](https://en.wikipedia.org/wiki/I%C2%B2C "I²C"), two [SPI](https://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus "Serial Peripheral Interface Bus") or one [I²S](https://en.wikipedia.org/wiki/I%C2%B2S "I²S"), one full-speed [USB](https://en.wikipedia.org/wiki/USB "USB") (only L0x2 and L0x3 chips).
    - one 12-bit [ADC](https://en.wikipedia.org/wiki/Analog-to-digital_converter "Analog-to-digital converter") with multiplexer, one 12-bit [DAC](https://en.wikipedia.org/wiki/Digital-to-analog_converter "Digital-to-analog converter"), two analog [comparators](https://en.wikipedia.org/wiki/Comparator "Comparator"), temperature sensor.
    - timers, low-power timers, [watchdog](https://en.wikipedia.org/wiki/Watchdog_timer "Watchdog timer") timers, 5 V-tolerant [GPIOs](https://en.wikipedia.org/wiki/General_Purpose_Input/Output "General Purpose Input/Output"), real-time clock, [DMA](https://en.wikipedia.org/wiki/Direct_memory_access "Direct memory access") controller, [CRC](https://en.wikipedia.org/wiki/Cyclic_redundancy_check "Cyclic redundancy check") engine.
    - capacitive touch sense and 32-bit random number generator (only L0x2 and L0x3 chips), [LCD](https://en.wikipedia.org/wiki/LCD "LCD") controller (only L0x3 chips), 128-bit [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard "Advanced Encryption Standard") engine (only L06x chips).
- [Oscillators](https://en.wikipedia.org/wiki/Electronic_oscillator "Electronic oscillator") consists of optional external 1 to 24 MHz crystal or oscillator, optional external 32.768 kHz crystal or ceramic resonator, multiple internal oscillators, and one PLL.
- IC [packages](https://en.wikipedia.org/wiki/Integrated_circuit_packaging "Integrated circuit packaging") are [LQFP](https://en.wikipedia.org/wiki/LQFP "LQFP")48, LQFP64, [TFBGA](https://en.wikipedia.org/wiki/Ball_grid_array "Ball grid array")64.
- Operating [voltage](https://en.wikipedia.org/wiki/IC_power_supply_pin "IC power supply pin") range is 1.8 to 3.6 [volt](https://en.wikipedia.org/wiki/Volt "Volt"), including a programmable [brownout](https://en.wikipedia.org/wiki/Brownout_(electricity) "Brownout (electricity)") detector.

### STM32 L1
The STM32 L1-series was the first group of STM32 microcontrollers with a primary goal of ultra-low power usage for battery-powered applications.

- Core:
    - [ARM Cortex-M3](https://en.wikipedia.org/wiki/ARM_Cortex-M3 "ARM Cortex-M3") core at a maximum clock rate of 32 [MHz](https://en.wikipedia.org/wiki/MHz "MHz").
- Memory:
    - [Static RAM](https://en.wikipedia.org/wiki/Static_RAM "Static RAM") consists of 10 / 16 / 32 / 48 / 80 KB general purpose, 80 bytes with tamper-detection erase.
    - Flash consists of 32 / 64 / 128 / 256 / 384 / 512 [KB](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") general purpose with [ECC](https://en.wikipedia.org/wiki/ECC_memory "ECC memory"), 4 / 8 KB system boot, 32 option bytes, [EEPROM](https://en.wikipedia.org/wiki/EEPROM "EEPROM") consists of 4 / 8 / 12 / 16 KB data storage with ECC.
    - Each chip has a factory-programmed 96-bit unique device identifier number.
- Peripherals:
    - Common peripherals included in all IC packages are USB 2.0 FS, two SPI, two I²C, three USART, eight 16-bit timers, two watchdog timers, temperature sensor, 16 to 24 channels into one ADC, two DACs, 37 to 83 GPIOs, seven DMA, real-time clock (RTC), cyclic redundancy check (CRC) engine. The STM32FL152 line adds a LCD controller.
- Oscillators consists of internal (16 MHz, 38 kHz, variable 64 kHz to 4 MHz), optional external (1 to 26 MHz, 32.768 to 1000 kHz).
- [IC packages](https://en.wikipedia.org/wiki/Integrated_circuit_packaging "Integrated circuit packaging"): UFQFPN48, [LQFP](https://en.wikipedia.org/wiki/LQFP "LQFP")48, LQFP64, [TFBGA](https://en.wikipedia.org/wiki/TFBGA "TFBGA")64, LQFP100, [UFBGA](https://en.wikipedia.org/wiki/UFBGA "UFBGA")100.
- Operating voltage range is 1.65 to 3.6 volt.


### STM32 L4
The STM32 L4-series is an evolution of STM32L1-series of ultra-low power microcontrollers. An example of L4 MCU is STM32L432KC in UFQFPN32 package, that has:

- ARM 32-bit Cortex-M4 core
- 80 MHz max CPU frequency
- VDD from 1.65 V to 3.6 V
- 256 KB Flash, 64 KB SRAM
- General purpose timers (4), SPI/I2S (2), I2C (2), USART (2), 12-bit ADC with 10 channels (1), GPIO (20) with external interrupt capability, RTC
- Random number generator (TRNG for HW entropy).
- Digital filter for [sigma-delta modulators](https://en.wikipedia.org/wiki/Delta-sigma_modulation "Delta-sigma modulation") (DFSDM) interface

### STM32 U0
The STM32 U0-series is an entry-level addition to the STM32-series of ultra-low power microcontrollers:

- ARM Cortex-M0+ core at a maximum clock rate of 56 MHz.
- Static consumption of 160 nA in standby mode with RTC (Real-Time Clock) and 16 nA in shutdown.
- Up to 256KB of Flash, package options up to 81 pins.
- Integrated LCD segment display controller.


## STM32F103x8

![[Pasted image 20240603224259.png]]
Blue Pill board (contains STM32F103C8T6 Microcontroller)

Arm® 32-bit Cortex®-M3 CPU core
– 72 MHz maximum frequency, 1.25 DMIPS/MHz (Dhrystone 2.1) performance
at 0 wait state memory access
– Single-cycle multiplication and hardware division
• Memories
– 64 or 128 Kbytes of Flash memory
– 20 Kbytes of SRAM
• Clock, reset and supply management
– 2.0 to 3.6 V application supply and I/Os
– POR, PDR, and programmable voltage detector (PVD)
– 4 to 16 MHz crystal oscillator
– Internal 8 MHz factory-trimmed RC
– Internal 40 kHz RC
– PLL for CPU clock
– 32 kHz oscillator for RTC with calibration
• Low-power
– Sleep, Stop and Standby modes
– VBAT supply for RTC and backup registers
• 2x 12-bit, 1 µs A/D converters (up to 16
channels)
– Conversion range: 0 to 3.6 V
– Dual-sample and hold capability
– Temperature sensor
• DMA
– 7-channel DMA controller
– Peripherals supported: timers, ADC, SPIs, I2Cs and USARTs
• Up to 80 fast I/O ports 
– 26/37/51/80 I/Os, all mappable on 16 external interrupt vectors and almost all 5 V-tolerant
Debug mode:
– Serial wire debug (SWD) and JTAG interfaces
• Seven timers
– Three 16-bit timers, each with up to 4 IC/OC/PWM or pulse counter and quadrature (incremental) encoder input
– 16-bit, motor control PWM timer with dead-time generation and emergency stop
– Two watchdog timers (independent and window)
– SysTick timer 24-bit downcounter
• Up to nine communication interfaces
– Up to two I2C interfaces (SMBus/PMBus®)
– Up to three USARTs (ISO 7816 interface,
LIN, IrDA capability, modem control)
– Up to two SPIs (18 Mbit/s)
– CAN interface (2.0B Active)
– USB 2.0 full-speed interface
• CRC calculation unit, 96-bit unique ID
• Packages are ECOPACK
![[Pasted image 20240603224941.png]]

# Understanding STM32 Naming Conventions# 

![[Pasted image 20240604220506.png]]
![[Pasted image 20240604220555.png]]
![[Pasted image 20240604220627.png]]
![[Pasted image 20240604220716.png]]
![[Pasted image 20240604220800.png]]
![[Pasted image 20240604220850.png]]
![[Pasted image 20240604220920.png]]

# Black Pill
The Black Pills are typically based on a STM32F401 or STM32F411 (both of the above are the F411 version) and offers the following specs:

- STM32F4 (STM32F401 or STM32F411) processor
- Same footprint (I/O pins)
- 25 MHz main crystal
- 32.768 kHz RTC crystal
- 512 kB Flash (STM32F411 version)
- 128 kB RAM
- 1 ADC (no DAC)
- USB-C connector
- Programming header

## PINOUT

![[Pasted image 20240604221434.png]]
Application 
• Motor drive and application control 
• Medical equipment 
• Industrial applications: PLC, inverters, circuit breakers 
• Printers, and scanners 
• Alarm systems, video intercom, and HVAC 
• Home audio appliances 
• Mobile phone sensor hub

STM32f411xC

The STM32F411XC/XE devices are based on the high-performance Arm® Cortex® -M4 32- bit RISC core operating at a frequency of up to 100 MHz. The Cortex®-M4 core features a floating-point unit (FPU) single precision, which supports all Arm single-precision data-processing instructions and data types. It also implements a full set of DSP instructions and a memory protection unit (MPU), which enhances application security.
The STM32F411xC/xE belongs to the STM32 Dynamic Efficiency product line (with products combining power efficiency, performance and integration) while adding a new innovative feature called Batch Acquisition Mode (BAM) allowing to save even more power consumption during data batching.

All devices offer one 12-bit ADC, a low-power RTC, six general-purpose 16-bit timers
including one PWM timer for motor control, two general-purpose 32-bit timers. They also
feature standard and advanced communication interfaces.
• Up to three I2Cs
• Five SPIs
• Five I2Ss out of which two are full duplex. To achieve audio class accuracy, the I2S
peripherals can be clocked via a dedicated internal audio PLL or via an external clock
to allow synchronization.
• Three USARTs
• SDIO interface
• USB 2.0 OTG full speed interface
The STM32F411xC/xE operate in the - 40 to + 125 °C temperature range from a 1.7 (PDR OFF) to 3.6 V power supply.

![[Pasted image 20240604222438.png]]

