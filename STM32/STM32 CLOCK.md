![[Pasted image 20240609183616.png]]

The STM32F401RE has the following four clock sources

LSI : Low Speed Internal  
LSE : Low Speed External  
HSI : High Speed Internal  
HSE : High Speed External

The LSI and LSE are used as low-speed 32.768(32)kHz clock sources.  
HSI and HSE are used as high-speed clock sources.

### 1. LSE (Low-Speed External)

- **Frequency**: Typically 32.768 kHz.
- **Source**: External crystal or resonator.
- **Use**: Used for real-time clock (RTC) operations due to its precision and low power consumption.
- **Characteristics**:
    - Very low frequency and power consumption.
    - High accuracy, typically used for maintaining timekeeping functions even in low-power modes.

### 2. HSE (High-Speed External)

- **Frequency**: Typically ranges from 4 MHz to 25 MHz.
- **Source**: External crystal, resonator, or oscillator.
- **Use**: Used for main system clock or precise timing requirements.
- **Characteristics**:
    - High accuracy and stability.
    - Suitable for applications requiring precise and high-frequency clocks.
    - Often used as the primary clock source for the system clock (SYSCLK) after potential PLL multiplication.

### 3. LSI (Low-Speed Internal)

- **Frequency**: Typically around 32 kHz.
- **Source**: Internal RC oscillator.
- **Use**: Used for watchdog timers (IWDG) and backup for RTC when LSE is not available.
- **Characteristics**:
    - Lower accuracy and stability compared to LSE.
    - Low power consumption.
    - Suitable for applications where precision timing is not critical.

### 4. HSI (High-Speed Internal)

- **Frequency**: Typically 8 MHz.
- **Source**: Internal RC oscillator.
- **Use**: Used as a fallback or default clock source during startup or when HSE is not available.
- **Characteristics**:
    - Moderate accuracy and stability.
    - Internal to the microcontroller, thus eliminating the need for external components.
    - Can be used directly or as a source for the PLL to achieve higher system clock frequencies.

### Comparison Summary

- **LSE vs. LSI**:
    
    - **LSE** is an external crystal with high accuracy and low power consumption, ideal for RTC.
    - **LSI** is an internal RC oscillator with lower accuracy, typically used for watchdog timers and backup RTC.
- **HSE vs. HSI**:
    
    - **HSE** is an external crystal or oscillator, providing high accuracy and stability, used for the main system clock.
    - **HSI** is an internal RC oscillator, providing moderate accuracy, used as a fallback or during startup.

### Typical Use Cases in an STM32 Microcontroller

- **LSE**: Real-time clock (RTC) for timekeeping functions.
- **HSE**: Main system clock for precise timing and high-performance applications.
- **LSI**: Watchdog timers and backup for RTC.
- **HSI**: Initial system startup and fallback clock source, general-purpose clocking when precision is less critical.

## RTC Clock Mux
- The RTC Clock Mux is located at the upper left of the system diagram.
- The RTC (Real-Time Clock) source multiplexer (MUX) in STM32 microcontrollers is a hardware feature that allows the microcontroller to select one of several available clock sources to drive the RTC.
- The RTC clock sources typically include:

	- **LSE (Low-Speed External)**: An external crystal or resonator, usually 32.768 kHz, known for high accuracy and low power consumption.
	- **LSI (Low-Speed Internal)**: An internal RC oscillator, typically around 32 kHz, which is less accurate than LSE but doesn't require external components.
	- **HSE/128 (High-Speed External divided by 128)**: An external high-speed clock (e.g., 8 MHz or higher) divided by 128 to bring it down to a suitable frequency for the RTC. This is less commonly used but can be useful if neither LSE nor LSI is available.
### What it Does

1. **Provides a Stable Clock for RTC**:
    
    - The RTC requires a stable and accurate clock source to maintain precise timekeeping, especially during low-power modes when the main system clock might be turned off.
    - The RTC source multiplexer allows the microcontroller to choose the best available clock source based on accuracy, power consumption, and availability.
2. **Enables Real-Time Clock Functionality**:
    
    - The RTC can keep track of the current time, date, and other time-related functions independently of the main processor.
    - It is essential for applications that require accurate timekeeping, such as clocks, alarms, timestamps, and low-power timekeeping.
3. **Facilitates Low-Power Operation**:
    
    - By selecting a low-power clock source like LSE or LSI, the microcontroller can maintain the RTC operation even in low-power modes, ensuring minimal power consumption.

### Practical Usage

Here’s a practical example of what the RTC source multiplexer does in a microcontroller application
#### Step-by-Step Configuration

1. **Enable Access to Backup Domain**:
    - The backup domain is a special area of the microcontroller that retains data even when the main power is off. To configure the RTC clock source, access to this domain must be enabled.
2. **Select the RTC Clock Source**:
    - Use the RTC source multiplexer to select the appropriate clock source (LSE, LSI, or HSE/128) for the RTC.
3. **Enable the RTC Clock**:
    - After selecting the clock source, enable the RTC clock so that the RTC can start operating.

## To IWDG Clock

To IWDG(kHz) is written just below RTC Clock Mux.
There is no choice here. The LSI is unconditionally used as the clock source.
IWDG is an independent watchdog timer.
Since we do not need much precision here, it makes no sense to use the LSI.
The fact that it is independent of the main clock system allows runaway detection even if there is a failure in the main clock.

## PLL(Phase Locked Loop)
- The Phase-Locked Loop (PLL) in STM32 microcontrollers is a critical component that enables the generation of high-frequency clock signals from lower-frequency sources. 
- The PLL (clock feedback control system) increases the clock frequency to satisfy the peripheral clock speed requirement. 
- A Phase-Locked Loop (PLL) is an electronic circuit used to generate a signal with a frequency that is a multiple of its input frequency. It works by comparing the phase of an input signal with that of a feedback signal derived from its output, and then adjusting its output to keep the phases aligned. This process effectively multiplies the input frequency, providing a stable and high-frequency clock signal.
### What Does the PLL Do?

1. **Frequency Multiplication**: The PLL can take a low-frequency clock source (such as an internal RC oscillator or an external crystal) and multiply it to achieve higher frequencies required by the system.
2. **Clock Generation**: Provides high-frequency clock signals for the CPU and peripherals, improving system performance.
3. **Stability and Accuracy**: Ensures that the generated clock signal is stable and accurate, which is crucial for reliable microcontroller operation.

PLL circuit
![[Pasted image 20240609214233.png]]
 Components:
 1. Phase Detector-
	- comparator that compares the phase input signal and feedback signal.
	- the output signal is the error signal that is the difference between input signal and feedback signal. 
2. Low pass filter- 
	- Removes high frequency noise from the output of phase-detector
	- Outputs a Dc voltage which is ripple free.
3. Amplifier-
	- Boosts the signal and provide adequete amplitude to the input signal.
	- The output of the amplifier is called the controlled voltage.
4. Voltage control-
	- The voltage controlled oscillator varies the output frequency according to the input voltage.
	- it has 3 state of operation
		- Free-running: When Vc is not applied. No control on output.
		- Capture: Comparison between input and output begins
		- Phase lock: input = output.

### Working Principle of PLL

1. **Initial State**:
    
    - The phase detector receives the reference clock and the feedback clock (initially free-running at VCO's natural frequency).
    - The error signal represents the phase difference between these clocks.
2. **Phase Comparison and Error Signal Generation**:
    
    - The phase detector continuously compares the phase of the reference clock with the feedback clock.
    - If there is a phase difference, the phase detector generates an error signal.
3. **Error Signal Filtering**:
    
    - The error signal passes through the low-pass filter, which smooths it to create a control voltage.
    - This control voltage represents the average phase difference over time.
4. **VCO Frequency Adjustment**:
    
    - The control voltage adjusts the VCO, changing its output frequency.
    - If the feedback clock lags the reference clock, the VCO speed increases; if it leads, the VCO speed decreases.
5. **Feedback Loop**:
    
    - The frequency divider scales down the VCO output to match the reference clock frequency.
    - The divided frequency is fed back to the phase detector.
6. **Locking Process**:
    
    - The loop iteratively adjusts the VCO frequency until the feedback clock is phase-locked with the reference clock.
    - When locked, the VCO output frequency is a stable multiple of the reference clock frequency.

### PLL in STM32 Microcontrollers

In STM32 microcontrollers, the PLL is used to multiply the frequency of an external or internal clock source to achieve a higher system clock frequency. Here's an example configuration process:

1. **Select and Enable Input Clock Source**:
    
    - Choose between HSE (High-Speed External) or HSI (High-Speed Internal).
    - Enable the selected clock source and wait for it to stabilize.
2. **Configure PLL Multiplication Factor**:
    
    - Set the multiplication factor to determine the desired output frequency.
    - The PLL source can be the HSE or HSI.
3. **Enable the PLL**:
    
    - Turn on the PLL and wait for it to lock.
4. **Switch System Clock to PLL Output**:
    
    - Once the PLL is stable, switch the system clock source to the PLL output.

### PLL Source MUX

The PLL source MUX in STM32 microcontrollers is a multiplexer that selects one of the available clock sources to feed into the PLL. This selection is crucial because it determines the base frequency that the PLL will multiply to generate the desired system clock frequency.

### Available Clock Sources for PLL

Typically, the available clock sources for the PLL in STM32 microcontrollers include:

1. **HSI (High-Speed Internal) Clock**: An internal RC oscillator with a default frequency (often 16 MHz).
2. **HSE (High-Speed External) Clock**: An external clock source, usually an external crystal or oscillator, with a typical frequency such as 8 MHz or 25 MHz.

### Function of the PLL Source MUX

The PLL source MUX allows you to choose between the HSI and HSE clocks to drive the PLL. This selection is made through specific configuration registers.

### Configuring the PLL Source MUX

1. **Enable the Chosen Clock Source**:
    
    - Ensure that the selected clock source (HSI or HSE) is enabled and stable before configuring the PLL.
2. **Select the PLL Source**:
    
    - Use the `RCC_PLLCFGR` register (or the equivalent in the specific STM32 model) to select the PLL source.
3. **Configure and Enable the PLL**:
    
    - Set the PLL multiplication and division factors.
    - Enable the PLL and wait for it to stabilize.
4. **Switch the System Clock to the PLL Output**:
    
    - Once the PLL is stable, switch the system clock to the PLL output.

## System clock MUX
The System Clock Multiplexer (System Clock MUX) is a mechanism that allows you to select the main clock source for the system. This selection determines the clock that drives the core and most of the peripherals. The System Clock MUX provides flexibility in choosing the best clock source for different application requirements, such as performance, power consumption, and accuracy.
### Available Clock Sources for System Clock MUX

The System Clock MUX typically allows you to select from the following clock sources:

1. **HSI (High-Speed Internal) Clock**: An internal RC oscillator, usually running at 16 MHz.
2. **HSE (High-Speed External) Clock**: An external crystal or oscillator, typically running at frequencies such as 8 MHz or 25 MHz.
3. **PLL (Phase-Locked Loop) Clock**: A high-frequency clock generated by multiplying the HSI or HSE clock.
4. **MSI (Multi-Speed Internal) Clock**: An internal clock that can run at multiple frequencies, commonly used in low-power modes(available in some STM32 families).

You can select the system clock from HSI, HSE, and PLL.

Of course, if you want to run at high frequencies, you should choose PLL.

Then, PCLK1 and PCLK2 are created from this output.

In the combo box marked with × 334 etc. (multiplication symbol), the number of multiplications of the PLL can be changed.

The combo box marked with / 4 etc. (with the division sign) allows you to divide the frequency.

It is possible to combine these to create an appropriate frequency.

If you make an unreasonable choice, that part will turn red and give you a warning.

## I2S Source Mux

You can select the clock source to I2S from PLLI2SCLK or EXT clock.

This part is grayed out, so I2S clocks can be enabled by setting the Mode of I2S2 or I2S3 to something other than Disable in the neighboring Pinout & Configuration –Category –Multimedia.

Ext clock is enabled by checking Audio Clock Input (I2S_CKIN) of Pinout & Configuration –Category –System Core –RCC.

To check this, you need to uncheck Master Clock Output 2.

## MCO1 source Mux
The Microcontroller Clock Output 1 (MCO1) source multiplexer (MUX) in STM32 microcontrollers allows you to select one of several internal clock sources to be output on the MCO1 pin. This feature is useful for debugging and for providing a clock signal to external components.

### Available Clock Sources for MCO1

Depending on the specific STM32 microcontroller, the MCO1 source MUX typically allows you to select from the following clock sources:

1. **HSI (High-Speed Internal) Clock**: An internal RC oscillator, usually running at 16 MHz.
2. **LSE (Low-Speed External) Clock**: An external low-speed clock, typically a 32.768 kHz crystal oscillator.
3. **HSE (High-Speed External) Clock**: An external crystal or oscillator, often running at 8 MHz or 25 MHz.
4. **PLL (Phase-Locked Loop) Clock**: The output clock from the PLL.

### Configuring the MCO1 Source MUX

To configure the MCO1 source MUX, you need to:

1. Select the desired clock source.
2. Configure the MCO1 prescaler (if needed) to adjust the frequency of the output clock.
3. Enable the MCO1 output.

### Typical Uses of MCO1

- **Providing a System Clock**: Supplying a clock to other peripherals or modules that require synchronization with the microcontroller.
- **Frequency Measurement**: Using external measurement tools to verify the frequency and stability of various internal clocks.
- **System Debugging**: Simplifying the process of debugging and verifying clock-related configurations by outputting the clock signal.

## MCO2 source Mux
The Microcontroller Clock Output 2 (MCO2) source multiplexer (MUX) in STM32 microcontrollers is similar to MCO1 but provides additional flexibility by allowing you to select another set of clock sources to be output on a different pin (typically PC9). This can be useful for applications that need to output multiple clock signals simultaneously.

### Available Clock Sources for MCO2

The available clock sources for MCO2 can vary depending on the specific STM32 microcontroller but generally include:

1. **System Clock (SYSCLK)**: The main system clock.
2. **PLLI2S Clock**: The clock generated by the PLLI2S (useful in applications that involve audio or other I2S peripherals).
3. **HSI (High-Speed Internal) Clock**: An internal RC oscillator, usually running at 16 MHz.
4. **HSE (High-Speed External) Clock**: An external crystal or oscillator, often running at 8 MHz or 25 MHz.
5. **PLL (Phase-Locked Loop) Clock**: The output clock from the main PLL.

### Function of MCO2

The MCO2 function allows you to output a selected internal clock signal on the MCO2 pin. This is useful for:

- **Clock Distribution**: Providing a clock signal to external devices or circuits that need to be synchronized with the microcontroller's clock system.
- **Testing and Debugging**: Measuring and verifying the frequency of internal clocks using external tools like oscilloscopes or frequency counters.
- **System Synchronization**: Synchronizing multiple devices or microcontrollers in a system by sharing a common clock signal.

### Configuring the MCO2 Source MUX

To configure the MCO2 source MUX, you need to:

1. Select the desired clock source.
2. Configure the MCO2 prescaler (if needed) to adjust the frequency of the output clock.
3. Enable the MCO2 output.

## STM32F401xD/xE block diagram
![[Pasted image 20240610223720.png]]