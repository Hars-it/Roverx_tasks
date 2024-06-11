Pulse Width Modulation, or PWM, is a commonly used technique for effectively controlling the power supplied to electrical devices. In order to attain a desired average voltage or power level, the principle of pulse width modulation (PWM) is used for a periodic signal, which is usually a square wave.

A key component of pulse width modulation (PWM) is the duty cycle, which is defined as the ratio of the pulse width to the whole time period. An increase in the duty cycle translates into an increase in average power output. Basically, PWM is used to obtain analog signals from digital services- for instance, the microcontrollers and it represents the amplitude of an analog signal input signal.

### Duty Cycle

One of the parameters of any square wave is duty cycle. Most square waves are 50%, this is the norm when discussing them, but they don’t have to be symmetrical. The ON time can be varied completely between signal being off to being fully on, 0% to 100%, and all ranges between.
![[Pasted image 20240529182916.png]]

### Frequency of PWM

The Speed at which something occurs over a specific time period is known as its frequency. In another way, the rate at which a vibration occurs that results in a wave, such as radio, light, or sound waves; this rate is usually measured in seconds. It is easy to define a frequency or period for regulating a particular servo.

Data is currently transmitted over communication channels using PWM’s duty cycle in an unambiguous communication system. PWM serves as a technique for converting high-frequency pulses into low-frequency output signals.

Frequency = 1 / Time Period

## Generation of PWM ##

- One possible output of a [monostable multivibrator](https://www.geeksforgeeks.org/astable-monostable-and-bistable-multivibrator/) is a PWM signal. When an external trigger is applied, a monostable multivibrator will only produce one output pulse and have one stable state. An operational amplifier comparator can be used to build a monostable multivibrator circuit.
	![[Screenshot 2024-05-29 184940.png]]
	
If THIGH is the duration for which the pulse is HIGH in one cycle and TLOW is the duration for which the pulse is LOW, then period of the pulse is

_**T = THIGH + TLOW**_

Duty Cycle = (THIGH / T) * 100

![[Screenshot 2024-05-29 185836.png]]
The pulse width is increasing when the modulating signal reaches its max value i.e. 4.5V and it decreases when the modulating signal decreases to its min value i.e. 1.5V. 
The width of the modulating signal depends on the amplitude of the modulating signal and the frequency of the carrier signal. Each pulse is triggered by a negative going pulse.
![[Screenshot 2024-05-29 190821.png]]
-Here the 555 IC is operating in a monostable mode.
-The modulating signal is applied at pin 5gets superimposed upon already existing 2/3Vcc at the inverting input of comparator A. The voltage at pin 5 varies from 4.5V to 1.5V instead of just 3.33V.v
The output of comparator A depends on the magnitude of the modulating signal. When the input to the non-inverting terminal of the comparator A is more than the reference voltage in the negative terminal (i.e. 4.5 to 1.5V), the output is high. 
 When the input to the inverting terminal of the comparator B i.e. the trigger voltage is more than the reference voltage in the positive terminal (i.e. 4.5 to 1.5V), the output is low.
 Hence for the input of 10 for the RS flipflop, Q' is high. Hence output through the inverter is low. Here the capacitor discharges. For 01 input in the RS flipflop, Q' is low. Hence the output through the inverter is high. Here the capacitor charges. For 00 input the output remains the same.
 ![[Pasted image 20240529194430.png]]

- Generation of PWM using a comparator and Saw Tooth generator
![[Pasted image 20240529201200.png]]
![[Pasted image 20240529201234.png]]
![[Pasted image 20240529201315.png]]

![[Pasted image 20240530205318.png]]
The received PWM signal is fed into the Pulse generator to remove the noise there by regenerating the PWM signal. The PWM signal is then goes to Ramp and pedestal generator where the slope ramp is equal pulse HIGH duration and greater the width of the pulse, higher the height of the Ramp. The PWM signal is also fed into reference pulse generator block which produces a train of constant width pulses synchronized to the leading edges of PWM. Then both the outputs are added and clipped
![[Pasted image 20240530205941.png]]
Then the PAM signal is passed through the LPF to get the original signal.

## PWM in Arduino ##

PWM, is a technique for getting analog results with digital means. Digital control is used to create a square wave, a signal switched between on and off. This on-off pattern can simulate voltages in between the full Vcc of the board (e.g., 5 V on UNO, 3.3 V on a MKR board) and off (0 Volts) by changing the portion of the time the signal spends on versus the time that the signal spends off. The duration of "on time" is called the pulse width. To get varying analog values, you change, or modulate, that pulse width. If you repeat this on-off pattern fast enough with an LED for example, the result is as if the signal is a steady voltage between 0 and Vcc controlling the brightness of the LED.
This duration or period is the inverse of the PWM frequency. In other words, with Arduino's PWM frequency at about 500Hz, the green lines would measure 2 milliseconds each. A call to [analogWrite](https://arduino.cc/en/Reference/AnalogWrite)() is on a scale of 0 - 255, such that  analogWrite(255) requests a 100% duty cycle (always on), and analogWrite(127)is a 50% duty cycle (on half the time) for example.
![[Pasted image 20240529201740.png]]

Arduino boards come with several pins capable of generating PWM signals. These pins are marked with a "~" symbol on the board, indicating their PWM capability. The number of PWM pins and their locations may vary depending on the specific Arduino model. 
PWM Pins on Arduino Uno: Arduino Uno, one of the most popular Arduino boards, has six PWM pins: 3, 5, 6, 9, 10, and 11.
The selection of specific pins for PWM functionality on Arduino boards is primarily determined by hardware considerations related to the microcontroller's architecture and pin capabilities.

Timer/Counter Register: Stores the current count value of the timer.
Control Registers: Configure the operating mode, clock source, and other parameters of the timer. Compare Match Registers: Used to trigger actions (e.g., generating PWM signals) when the timer count matches a specific value.

Role of Timers in Generating PWM Signals: Timer modules are essential for generating PWM signals in Arduino. They facilitate the precise timing required to produce PWM waveforms with accurate duty cycles and frequencies. Here's how timers contribute to PWM generation: 
Clock Source Selection: Timer modules can be configured to use different clock sources, such as the system clock (CPU frequency) or an external clock. The clock frequency determines the resolution and frequency of the PWM signals generated by the timer. 
Timer Counting: Timer modules increment or decrement a counter register at each clock pulse, effectively measuring time. The counting behavior can be configured based on the specific application requirements, including the counting direction (up or down) and the counting range (maximum count value). 
Compare Match Output: Timer modules support compare match functionality, where the current count value is compared against predefined values stored in compare match registers. When the count value matches a compare match value, a hardware event, such as toggling an output pin or triggering an interrupt, can be generated. 
PWM Generation: PWM signals are generated by modulating the output state of a pin based on the timer's count value and compare match functionality. By adjusting the compare match value dynamically, the duty cycle of the PWM signal can be controlled, thereby regulating the average voltage or current applied to the load.

PWM GENERATION USING TIMERS 
Waveform Generation Mode bits (WGM): these control the overall mode of the timer. (These bits are split between TCCRnA and TCCRnB.) 
Clock Select bits (CS): these control the clock prescaler Compare Match Output A Mode bits (COMnA): these enable/disable/invert output A Compare Match Output B Mode bits 
(COMnB): these enable/disable/invert output B The Output Compare Registers OCRnA and OCRnB set the levels at which outputs A and B will be affected. multiple compare is used so that we can generate multiple PWM signal using same timer 

FAST PWM: 
In the simplest PWM mode, the timer repeatedly counts from 0 to 255. The output turns on when the timer is at 0, and turns off when the timer matches the output compare register. The higher the value in the output compare register, the higher the duty cycle. This mode is known as Fast PWM Mode
![[Pasted image 20240530232535.png]]

Phase-Correct PWM: 
The second PWM mode is called phase-correct PWM. In this mode, the timer counts from 0 to 255 and then back down to 0. The output turns off as the timer hits the output compare register value on the way up, and turns back on as the timer hits the output compare register value on the way down. The result is a more symmetrical output.
![[Pasted image 20240530232644.png]]
The TCCRnA and TCCRnB registers are used in AVR microcontrollers, such as the ATmega328P on the Arduino Uno, to configure and control the Timer/Counter modules. Each Timer/Counter module (e.g., Timer0, Timer1, Timer2) has its own set of these registers. The 'n' in TCCRnA and TCCRnB refers to the timer number.

### TCCRnA Register

The TCCRnA (Timer/Counter Control Register A) is used to control specific modes and functions of the timer. The precise functions of the bits within this register depend on the timer and the mode of operation.
#### Timer/Counter 0 (8-bit) TCCR0A Register

- **COM0A1, COM0A0**: Compare Output Mode for Channel A. Controls the behavior of the OC0A pin (e.g., set, clear, or toggle on compare match).
- **COM0B1, COM0B0**: Compare Output Mode for Channel B. Controls the behavior of the OC0B pin.
- **WGM01, WGM00**: Waveform Generation Mode. Sets the timer's mode of operation (e.g., Normal, PWM, CTC).
#### Timer/Counter 1 (16-bit) TCCR1A Register

- **COM1A1, COM1A0**: Compare Output Mode for Channel A.
- **COM1B1, COM1B0**: Compare Output Mode for Channel B.
- **WGM11, WGM10**: Waveform Generation Mode bits (combined with WGM12 and WGM13 in TCCR1B for additional modes).

![[Screenshot 2024-06-01 030412.png]]

![[Screenshot 2024-06-01 030355.png]]

![[Screenshot 2024-06-01 030447.png]]

COMnA[1:0] : Compare Match Output Mode for Channel A. These bits determine the action taken when a compare match occurs on Channel A (e.g., toggling, clearing, setting the output). 

COMnB[1:0] : Compare Match Output Mode for Channel B. Similar to COMnA but for Channel B. 

WGMn[1:0] : Waveform Generation Mode. These bits specify the operation mode of the timer, including PWM modes (e.g., Fast PWM, Phase Correct PWM) and other waveform generation modes.

### TCCRnB Register

TCCRnB configures the clock source and prescaler settings for the timer. It contains bits for setting the clock source (CSn[2:0]) and configuring the prescaler, which determines the frequency of the timer clock

CSn2, CSn1, CSn0 (Clock Select Bits): 
- These three bits (CSn[2:0]) determine the clock source for the timer/counter. 
- The clock source options vary depending on the specific microcontroller and timer module being used. 
- Different combinations of these bits select different clock sources, such as the system clock (CPU frequency), an external clock source, or a divided version of the system clock. 
- The clock source directly influences the frequency of the timer/counter, which, in turn, affects the PWM signal's frequency and resolution. 
- Here are some common clock source configurations: 
	- CSn2 = 0, CSn1 = 0, CSn0 = 0: No clock source (timer stopped). 
	- CSn2 = 0, CSn1 = 0, CSn0 = 1: System clock (no pre-scaling). 
	- CSn2 = 0, CSn1 = 1, CSn0 = 0: System clock divided by 8. 
	- CSn2 = 0, CSn1 = 1, CSn0 = 1: System clock divided by 64. 
	- CSn2 = 1, CSn1 = 0, CSn0 = 0: External clock on Tn pin (rising edge). 
	- CSn2 = 1, CSn1 = 0, CSn0 = 1: External clock on Tn pin (falling edge). 
	- CSn2 = 1, CSn1 = 1, CSn0 = 0: System clock divided by 256. 
	- CSn2 = 1, CSn1 = 1, CSn0 = 1: System clock divided by 1024

FOCnA and FOCnB:
1. FOCnA (Force Output Compare A): 
	- This bit, when set to 1, forces the output compare action for Output Compare Unit A of the timer associated with the specific register (e.g., Timer/Counter n). 
	- When FOCnA is set, it causes the action specified by the COMnA[1:0] bits in the Timer/Counter Control Register A (TCCRnA) to occur immediately, regardless of the current count value of the timer. 
	- Typically, this action involves toggling or setting/resetting the PWM output pin associated with Output Compare Unit A, depending on the configuration specified by the COMnA bits.

3. FOCnB (Force Output Compare B): 
	- Similar to FOCnA, FOCnB is associated with Output Compare Unit B of the timer. 
	- When FOCnB is set to 1, it forces the output compare action specified by the COMnB[1:0] bits in the Timer/Counter Control Register A (TCCRnA) to occur immediately, regardless of the current count value of the timer. 
	- Like FOCnA, the action triggered by FOCnB typically involves toggling or setting/resetting the PWM output pin associated with Output Compare Unit B.

The main purpose of the FOCnA and FOCnB bits is to provide a mechanism for manually triggering the output compare action on specific PWM output pins. This can be useful in certain scenarios where immediate control over the PWM output state is required

OUTPUT COMPARE REGISTERS(OCRnA and OCRnB)

Timer/counter0(8-bit)

- OCR0A: Output Compare Register A for Timer/Counter0 
- OCR0B: Output Compare Register B for Timer/Counter0 

These registers are used to generate PWM signals or trigger an action at a specific timer count value. For example, in CTC mode, the timer counts up to the value in OCR0A and then resets, which can be used to create precise time intervals

Timer/counter1(16-bit)

- OCR1A: Output Compare Register A for Timer/Counter1 
- OCR1B: Output Compare Register B for Timer/Counter1 

Being a 16-bit timer, Timer1 can handle larger values and longer timing intervals than the 8-bit timers. The OCR1A and OCR1B registers are particularly useful for applications requiring higher precision and longer delays, such as servo control or high-resolution PWM.

Timer/counter2(8-bit)

- OCR2A: Output Compare Register A for Timer/Counter2 
- OCR2B: Output Compare Register B for Timer/Counter2 

Similar to Timer0, Timer2 is also an 8-bit timer but operates independently, which allows for more flexibility in applications requiring multiple timers.

1) TIMSKn (Timer/Counter Interrupt Mask Register): 
	- OCIEnA/B (Timer/Counter n Output Compare Match A/B Interrupt Enable): These bits enable/disable the Timer/Counter n Output Compare A and B Match Interrupt. 
	- TOIEn (Timer/Counter n Overflow Interrupt Enable): This bit enables/disables the Timer/Counter n Overflow Interrupt. 
	- OCIEnA (Timer/Counter n Output Compare Match A Interrupt Enable): This bit enables/disables the Timer/Counter n Output Compare Match A Interrupt. 
2) TIFRn (Timer/Counter Interrupt Flag Register): 
	- OCFnA/B (Output Compare A/B Match Flag for Timer/Counter n): These bits get set when an output compare match occurs between the Timer/Counter n output and the contents of the compare register A or B. 
	- TOVn (Timer/Counter n Overflow Flag): This bit is set when Timer/Counter n overflows. 
	- OCFnA (Output Compare Match Flag for Timer/Counter n): This bit gets set when an output compare match occurs between the Timer/Counter n output and the contents of the compare register A.

PWM modes in atmega328

Timer modes:
1. Normal Mode: The timer counts from 0 to its maximum value and then overflows. 
2. CTC (Clear Timer on Compare Match) Mode: The timer is cleared to 0 when it matches a compare value. 
3. Fast PWM Mode: Used for Pulse Width Modulation with high-frequency output. 
4. Phase Correct PWM Mode: Generates a PWM signal with frequency controlled by a compare value.


Timer/counter0

Fast PWM mode
- Description: The counter counts from 0 to 255 and then resets to 0. The output compare registers (OCR0A and OCR0B) determine the duty cycle. 
- Registers: TCCR0A : Set WGM00 and TCCR0B : Set WGM01 for Fast PWM. CS bits for prescaling

// Set Timer0 to Fast PWM mode on PD6 (OC0A)
void setup() {
  // Set PD6 (pin 6 on Arduino) as output
  DDRD |= (1 << DDD6);

  // Set Fast PWM mode, non-inverting
  TCCR0A |= (1 << COM0A1) | (1 << WGM01) | (1 << WGM00);

  // Start the timer with no prescaling
  TCCR0B |= (1 << CS00);
  
  // Set compare match value for 50% duty cycle
  OCR0A = 127;
}

void loop() {
  // Main loop does nothing, PWM is handled by hardware
}

Phase correct PWM
- Description: The counter counts from 0 to 255 and then back down to 0, creating a symmetrical PWM signal. 
- Registers: TCCR0A : Set WGM00 . TCCR0B : Set CS bits for prescaling.

// Example code to configure Timer0 for Phase Correct PWM on PD6 (OC0A)

void setup() {
  // Set PD6 (Arduino pin 6) as output
  DDRD |= (1 << DDD6);

  // Configure Timer0 for Phase Correct PWM
  // Clear OC0A on compare match when up-counting, set OC0A on compare match when down-counting
  TCCR0A |= (1 << COM0A1);
  TCCR0A &= ~(1 << COM0A0);
  
  // Set Waveform Generation Mode to Phase Correct PWM (WGM00 = 1, WGM01 = 0)
  TCCR0A |= (1 << WGM00);
  TCCR0A &= ~(1 << WGM01);
  TCCR0B &= ~(1 << WGM02);

  // Set prescaler to 64 and start the timer
  TCCR0B |= (1 << CS01) | (1 << CS00);
  TCCR0B &= ~(1 << CS02);

  // Set duty cycle to 50%
  OCR0A = 127; // 50% of 255 (8-bit resolution)
}

void loop() {
  // Main loop does nothing, PWM is handled by hardware
}


Timer/counter1(16-bit)

Fast PWM
- Description: Provides higher resolution PWM using a 16-bit counter. 
- Registers: 
	- TCCR1A : Set WGM10 and WGM11 . 
	- TCCR1B : Set WGM12 and WGM13 , and set CS bits for prescaling


void setup() {
  // Set PB1 (Arduino pin 9) as output
  DDRB |= (1 << DDB1);

  // Configure Timer1 for Fast PWM
  // Clear OC1A on compare match, set OC1A at BOTTOM (non-inverting mode)
  TCCR1A |= (1 << COM1A1);
  TCCR1A &= ~(1 << COM1A0);
  
  // Set Fast PWM mode with ICR1 as TOP (WGM13:0 = 14)
  TCCR1A |= (1 << WGM11);
  TCCR1B |= (1 << WGM13) | (1 << WGM12);
  TCCR1A &= ~(1 << WGM10);
  TCCR1B &= ~(1 << WGM10);
  
  // Set TOP value for a 16-bit counter
  ICR1 = 39999; // for 50Hz PWM with 16MHz clock and 8 prescaler
  
  // Set compare match value for 50% duty cycle
  OCR1A = 19999;

  // Start the timer with prescaler 8
  TCCR1B |= (1 << CS11);
  TCCR1B &= ~(1 << CS12) & ~(1 << CS10);
}

void loop() {
  // Main loop does nothing, PWM is handled by hardware
}

Phase correct PWM

- Description: Similar to Fast PWM but the counter counts up and down, providing symmetrical PWM. 
- Registers: 
	- TCCR1A : Set WGM10 and WGM11
	- TCCR1B : Set CS bits for prescaling.

// Set Timer1 to Phase Correct PWM mode on PB1 (OC1A)
void setup() {
  // Set PB1 (pin 9 on Arduino) as output
  DDRB |= (1 << DDB1);

  // Set Phase Correct PWM mode, non-inverting
  TCCR1A |= (1 << COM1A1) | (1 << WGM10);

  // Start the timer with no prescaling
  TCCR1B |= (1 << CS10);
  
  // Set compare match value for 50% duty cycle
  OCR1A = 32767;
}

void loop() {
  // Main loop does nothing, PWM is handled by hardware
}

Timer/couter2(8-bit)

Fast PWM mode

- Description: Similar to Timer0 Fast PWM but uses Timer2. 
- Registers: 
	- TCCR2A : Set WGM20 and WGM21.
	- TCCR2B : Set CS bits for prescaling.

// Example code to configure Timer2 for Fast PWM on PB3 (OC2A)

void setup() {
  // Set PB3 (Arduino pin 11) as output
  DDRB |= (1 << DDB3);

  // Configure Timer2 for Fast PWM
  // Clear OC2A on compare match, set OC2A at BOTTOM (non-inverting mode)
  TCCR2A |= (1 << COM2A1);
  TCCR2A &= ~(1 << COM2A0);
  
  // Set Fast PWM mode (WGM22:0 = 011)
  TCCR2A |= (1 << WGM21) | (1 << WGM20);
  TCCR2B &= ~(1 << WGM22);
  
  // Set compare match value for 50% duty cycle
  OCR2A = 127; // 50% of 255 (8-bit resolution)

  // Start the timer with prescaler 64
  TCCR2B |= (1 << CS22);
  TCCR2B &= ~(1 << CS21) & ~(1 << CS20);
}

void loop() {
  // Main loop does nothing, PWM is handled by hardware
}

Phase-correct PWMmode

- Description: Similar to Timer0 Phase Correct PWM but uses Timer2. 
- Registers: 
	- TCCR2A : Set WGM20 . 
	- TCCR2B : Set CS bits for prescaling.

// Example code to configure Timer2 for Phase Correct PWM on PB3 (OC2A)

void setup() {
  // Set PB3 (Arduino pin 11) as output
  DDRB |= (1 << DDB3);

  // Configure Timer2 for Phase Correct PWM
  // Clear OC2A on compare match when up-counting, set OC2A on compare match when down-counting
  TCCR2A |= (1 << COM2A1);
  TCCR2A &= ~(1 << COM2A0);
  
  // Set Phase Correct PWM mode (WGM22:0 = 001)
  TCCR2A |= (1 << WGM20);
  TCCR2A &= ~(1 << WGM21);
  TCCR2B &= ~(1 << WGM22);

  // Set compare match value for 50% duty cycle
  OCR2A = 127; // 50% of 255 (8-bit resolution)

  // Start the timer with prescaler 64
  TCCR2B |= (1 << CS22);
  TCCR2B &= ~(1 << CS21) & ~(1 << CS20);
}

void loop() {
  // Main loop does nothing, PWM is handled by hardware
}

## Practical Applications

### LED Dimming

By adjusting the duty cycle of the PWM signal, you can vary the brightness of an LED. This is commonly used in lighting applications.

### Motor Speed Control

PWM is used to control the speed of DC motors. By changing the duty cycle, the average voltage applied to the motor changes, thus controlling its speed.

### Signal Generation

PWM can be used to generate various types of waveforms for testing and other purposes. By adjusting the frequency and duty cycle, different signals can be created.

### Applications of PWM in Data Transfer

1. **Infrared Communication:**
    
    - PWM is used in remote controls to transmit data via infrared light. The remote control sends a PWM signal with varying duty cycles corresponding to different commands.
    - Example: A 30% duty cycle might represent the "Volume Up" command, while a 60% duty cycle might represent the "Channel Up" command.
2. **Radio Frequency (RF) Communication:**
    
    - In RF communication, PWM can be used to modulate the carrier signal, enabling data transmission over a wireless medium.
    - Example: RF modules like ASK (Amplitude Shift Keying) use PWM to encode data for transmission.
3. **Optical Communication:**
    
    - PWM is used in fiber optics and other optical communication methods to transmit data by varying the light intensity.
    - Example: Digital data can be transmitted over a fiber optic cable by modulating the light intensity using PWM.
4. **Motor Control with Feedback:**
    
    - In motor control systems, PWM signals can carry feedback information from sensors to the controller, which adjusts the motor's speed or position accordingly.

### Implementation Example: Infrared Remote Control

Here’s an example of how PWM can be used in an infrared remote control system to transmit data:

1. **Encoding Data:**
    
    - Different commands are assigned unique PWM duty cycles. For instance:
        - 10% duty cycle for "Power On"
        - 20% duty cycle for "Volume Up"
        - 30% duty cycle for "Channel Up"
2. **Transmitting Data:**
    
    - The remote control uses an infrared LED to emit light modulated by the PWM signal.
    - The receiver detects the PWM signal and decodes the duty cycle to determine the command.

### Example Code: Sending Data via PWM

Here's an example of how to implement a simple PWM-based data transmitter using an Arduino:

const int pwmPin = 9; // PWM pin to output the signal

void setup() {
  // Set the PWM pin as an output
  pinMode(pwmPin, OUTPUT);
}

void loop() {
  // Send "Power On" command (10% duty cycle)
  sendCommand(10);
  delay(1000); // Wait for 1 second
  
  // Send "Volume Up" command (20% duty cycle)
  sendCommand(20);
  delay(1000); // Wait for 1 second
  
  // Send "Channel Up" command (30% duty cycle)
  sendCommand(30);
  delay(1000); // Wait for 1 second
}

void sendCommand(int dutyCycle) {
  // Set the duty cycle
  analogWrite(pwmPin, (255 * dutyCycle) / 100);
}

### Example Code: Receiving Data via PWM

Here's an example of how to implement a simple PWM-based data receiver using an Arduino:

const int pwmPin = 2; // PWM pin to input the signal

void setup() {
  // Set the PWM pin as an input
  pinMode(pwmPin, INPUT);
  Serial.begin(9600); // Start serial communication for debugging
}

void loop() {
  int value = pulseIn(pwmPin, HIGH); // Measure the length of the HIGH pulse
  int dutyCycle = map(value, 0, 255, 0, 100); // Map the pulse length to a duty cycle
  Serial.println(dutyCycle); // Print the duty cycle for debugging

  // Decode the command based on the duty cycle
  if (dutyCycle >= 9 && dutyCycle <= 11) {
    Serial.println("Command: Power On");
  } else if (dutyCycle >= 19 && dutyCycle <= 21) {
    Serial.println("Command: Volume Up");
  } else if (dutyCycle >= 29 && dutyCycle <= 31) {
    Serial.println("Command: Channel Up");
  }
}
