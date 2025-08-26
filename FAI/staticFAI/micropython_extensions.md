# micropython_extensions.md - CORE support for micropython specific extensions
# [SYSTEM FILE - DO NOT REMOVE]

# MicroPython Extensions - Hardware Programming

**Note:** MicroPython shares most syntax with standard Python but adds hardware-specific capabilities for microcontroller programming.

---

# MicroPython = Python + Hardware [KNOW]

## Shared Syntax and Concepts
All these work the same in MicroPython:
- Variables and data types
- Control structures (if/else, loops)
- Functions and basic operations
- Lists, strings, and basic data structures
- Import statements
- Comments and basic script structure

## Key Differences from Standard Python
1. **Hardware interaction** through machine library
2. **Continuous execution** model (like Arduino)
3. **Memory constraints** - more limited than desktop Python
4. **Real-time requirements** for hardware control

---

# Arduino-Style Programming Structure [KNOW]

## Setup() and Loop() Equivalent
Unlike Arduino, MicroPython doesn't have built-in setup() and loop() functions. Create this pattern manually:

```python
# MicroPython continuous execution pattern
from machine import Pin
import time

# Setup section (runs once)
led = Pin(25, Pin.OUT)    # Built-in LED on Pico
button = Pin(14, Pin.IN, Pin.PULL_DOWN)

# Main loop (runs continuously)
while True:
    if button.value():
        led.toggle()
        time.sleep(0.5)   # Debounce delay
```

**Comparison with Arduino:**
```cpp
// Arduino equivalent
void setup() {
  pinMode(25, OUTPUT);
  pinMode(14, INPUT_PULLDOWN);
}

void loop() {
  if (digitalRead(14)) {
    digitalWrite(25, !digitalRead(25));
    delay(500);
  }
}
```

---

# Machine Library [KNOW]

## Digital I/O with Pin Objects [KNOW]

### Creating Pin Objects
```python
from machine import Pin

# Output pin (LED)
led = Pin(15, Pin.OUT)

# Input pin with pull-down resistor
button = Pin(14, Pin.IN, Pin.PULL_DOWN)

# Input pin with pull-up resistor  
switch = Pin(16, Pin.IN, Pin.PULL_UP)
```

### Digital Operations [KNOW]
```python
# Writing to outputs
led.on()           # Set pin HIGH (3.3V)
led.off()          # Set pin LOW (0V)  
led.toggle()       # Switch between HIGH/LOW
led.value(1)       # Set to HIGH
led.value(0)       # Set to LOW

# Reading from inputs
button_state = button.value()    # Returns 1 or 0
if button.value():
    print("Button pressed")
```

### Complete Digital I/O Example
```python
from machine import Pin
import time

# Setup
led = Pin(25, Pin.OUT)                    # Onboard LED
external_led = Pin(15, Pin.OUT)           # External LED
button = Pin(14, Pin.IN, Pin.PULL_DOWN)   # Button input

# Main loop
while True:
    if button.value():
        led.on()
        external_led.toggle()
        time.sleep(0.2)
    else:
        led.off()
        time.sleep(0.1)
```

---

# Analog Operations [KNOW]

## Analog to Digital Converter (ADC) [KNOW]
```python
from machine import Pin, ADC
import time

# Create ADC object on pin 26
potentiometer = ADC(Pin(26))

while True:
    # Read raw value (0-65535)
    raw_value = potentiometer.read_u16()
    
    # Convert to voltage (0-3.3V)  
    voltage = raw_value * 3.3 / 65535
    
    print(f"Raw: {raw_value}, Voltage: {voltage:.2f}V")
    time.sleep(1)
```

## Pulse Width Modulation (PWM) [KNOW]
```python
from machine import Pin, PWM
import time

# Create PWM object
led_pwm = PWM(Pin(15))
led_pwm.freq(1000)  # Set frequency to 1kHz

# Fade LED in and out
while True:
    # Fade up
    for brightness in range(0, 65536, 1000):
        led_pwm.duty_u16(brightness)
        time.sleep(0.05)
    
    # Fade down  
    for brightness in range(65535, -1, -1000):
        led_pwm.duty_u16(brightness)
        time.sleep(0.05)
```

---

# Servo Motor Control [KNOW]

## Basic Servo Operations [KNOW]
```python
from machine import Pin, PWM
import time

# Create PWM servo controller on pin 16
servo = PWM(Pin(16))
servo.freq(50)  # 50Hz frequency for servo control

def set_servo_angle(angle):
    """Set servo to specific angle (0-180 degrees)"""
    # Convert angle to duty cycle
    # Servo expects 1-2ms pulse width (1000-2000 microseconds)
    if 0 <= angle <= 180:
        duty = int((angle / 180) * 1000 + 1000)
        servo.duty_us(duty)
    else:
        print("Angle must be between 0 and 180 degrees")

# Example: Servo sweep demonstration
print("Northeastern engineering servo demo starting...")

while True:
    print("Sweeping left to right...")
    for angle in range(0, 181, 15):
        set_servo_angle(angle)
        print(f"Servo at {angle} degrees")
        time.sleep(0.2)
    
    print("Sweeping right to left...")
    for angle in range(180, -1, -15):
        set_servo_angle(angle)
        print(f"Servo at {angle} degrees")
        time.sleep(0.2)
```

## Advanced Servo Control [KNOW]
```python
from machine import Pin, PWM, ADC
import time

# Setup servo and potentiometer for manual control
servo = PWM(Pin(16))
servo.freq(50)
pot = ADC(Pin(26))  # Potentiometer for manual control

def set_servo_angle(angle):
    """Convert angle to appropriate duty cycle"""
    if 0 <= angle <= 180:
        duty = int((angle / 180) * 1000 + 1000)
        servo.duty_us(duty)
    return angle

print("Manual servo control - turn potentiometer to control servo")

while True:
    # Read potentiometer (0-65535)
    pot_reading = pot.read_u16()
    
    # Convert to servo angle (0-180 degrees)
    angle = (pot_reading / 65535) * 180
    
    # Set servo position
    actual_angle = set_servo_angle(angle)
    print(f"Potentiometer: {pot_reading}, Servo angle: {actual_angle:.1f}°")
    
    time.sleep(0.1)  # Small delay for smooth operation
```

---

# Time Functions [KNOW]

## Essential Timing
```python
import time

time.sleep(1)           # Sleep for 1 second
time.sleep_ms(500)      # Sleep for 500 milliseconds
time.sleep_us(1000)     # Sleep for 1000 microseconds

# Get current time (milliseconds since boot)
start_time = time.ticks_ms()
# ... do something ...
elapsed = time.ticks_diff(time.ticks_ms(), start_time)
print(f"Elapsed: {elapsed}ms")
```

---

# Built-in Functions [KNOW]

## Accessing Python Built-ins
```python
# Must import builtins for some standard Python functions
import builtins

# Now you can use standard Python functions
numbers = [1, 2, 3, 4, 5]
total = builtins.sum(numbers)
maximum = builtins.max(numbers)
print(f"Sum: {total}, Max: {maximum}")
```

---

# Common Hardware Patterns [KNOW]

## Button with LED Control
```python
from machine import Pin
import time

led = Pin(15, Pin.OUT)
button = Pin(14, Pin.IN, Pin.PULL_DOWN)

led_state = False
last_button_state = False

while True:
    current_button_state = button.value()
    
    # Detect button press (rising edge)
    if current_button_state and not last_button_state:
        led_state = not led_state
        led.value(led_state)
        time.sleep(0.05)  # Debounce
    
    last_button_state = current_button_state
    time.sleep(0.01)
```

## Analog Sensors: Photoresistor and Thermistor [KNOW]
```python
from machine import Pin, ADC
import time

# Setup analog sensors
photoresistor = ADC(Pin(26))  # Light sensor
thermistor = ADC(Pin(27))     # Temperature sensor
status_led = Pin(25, Pin.OUT)

def read_light_level():
    """Read photoresistor and return light level percentage"""
    raw_value = photoresistor.read_u16()
    light_percent = (raw_value / 65535) * 100
    return light_percent

def read_temperature():
    """Read thermistor and estimate temperature (simplified)"""
    raw_value = thermistor.read_u16()
    # Simplified temperature conversion (actual formula depends on thermistor)
    voltage = raw_value * 3.3 / 65535
    # Approximate temperature for common thermistor
    temp_c = (voltage - 0.5) * 100  # Simplified linear approximation
    return temp_c

# Northeastern weather station example
print("Northeastern Campus Weather Monitor")
print("Monitoring conditions near Snell Library...")

while True:
    light = read_light_level()
    temp = read_temperature()
    
    print(f"Light Level: {light:.1f}%")
    print(f"Temperature: {temp:.1f}°C")
    
    # Turn on LED if it's dark and cold (typical Boston winter)
    if light < 30 and temp < 10:
        status_led.on()
        print("Cold and dark - typical Boston winter day!")
    else:
        status_led.off()
    
    print("-" * 30)
    time.sleep(2)
```

---

# Communication Protocols [MAYBE]

## I2C Communication [MAYBE]
```python
from machine import Pin, I2C

# Create I2C object
i2c = I2C(0, scl=Pin(17), sda=Pin(16), freq=400000)

# Scan for devices
devices = i2c.scan()
print(f"I2C devices found: {devices}")

# Basic I2C read/write (device-specific)
# i2c.writeto(address, data)
# data = i2c.readfrom(address, num_bytes)
```

## SPI Communication [MAYBE]
```python
from machine import Pin, SPI

# Create SPI object
spi = SPI(0, baudrate=1000000, polarity=0, phase=0, 
          sck=Pin(18), mosi=Pin(19), miso=Pin(16))

# Basic SPI operations (device-specific)
# spi.write(data)
# response = spi.read(num_bytes)
```
