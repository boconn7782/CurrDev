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
# **[ADDED BY AI - REVIEW]** - Multiple analog sensor reading
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

# **[ADDED BY AI - REVIEW]** - Northeastern weather station
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

## Serial Communication and Monitoring [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - Serial data logging for engineering projects
from machine import Pin, ADC
import time

# Setup for data collection
sensor = ADC(Pin(26))
led = Pin(25, Pin.OUT)

def log_sensor_data():
    """Log sensor data in format suitable for MATLAB import"""
    timestamp = time.ticks_ms()
    sensor_value = sensor.read_u16()
    voltage = sensor_value * 3.3 / 65535
    
    # Print in CSV format for easy data analysis
    print(f"{timestamp},{sensor_value},{voltage:.3f}")
    
    return voltage

# **[ADDED BY AI - REVIEW]** - Data collection for ENGR project
print("Northeastern Engineering Data Logger")
print("Time(ms),Raw_Value,Voltage(V)")  # CSV header for MATLAB

# Collect data for 30 seconds
start_time = time.ticks_ms()
sample_count = 0

while time.ticks_diff(time.ticks_ms(), start_time) < 30000:  # 30 seconds
    voltage = log_sensor_data()
    
    # Blink LED to show data collection active
    led.toggle()
    
    sample_count += 1
    time.sleep(0.1)  # 10 samples per second

print(f"# Data collection complete: {sample_count} samples")
led.off()
```

---

# Advanced Hardware Topics [MAYBE]

## Servo Motor Control [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - Complete servo control example
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

# **[ADDED BY AI - REVIEW]** - Northeastern-themed servo example
print("Northeastern Husky head tracker starting...")

# Sweep servo like a husky watching a hockey puck
while True:
    print("Tracking puck left to right...")
    for angle in range(0, 181, 15):
        set_servo_angle(angle)
        print(f"Husky looking at {angle} degrees")
        time.sleep(0.2)
    
    print("Tracking puck right to left...")
    for angle in range(180, -1, -15):
        set_servo_angle(angle)
        print(f"Husky looking at {angle} degrees")
        time.sleep(0.2)
```

## Ultrasonic Distance Sensor [KNOW]
```python
# **[ADDED BY AI - REVIEW]** - HC-SR04 ultrasonic sensor
from machine import Pin
import time

# Setup ultrasonic sensor pins
trigger = Pin(2, Pin.OUT)
echo = Pin(3, Pin.IN)

def measure_distance():
    """Measure distance in centimeters using ultrasonic sensor"""
    # Send trigger pulse
    trigger.off()
    time.sleep_us(2)
    trigger.on()
    time.sleep_us(10)
    trigger.off()
    
    # Wait for echo
    while echo.value() == 0:
        pulse_start = time.ticks_us()
    while echo.value() == 1:
        pulse_end = time.ticks_us()
    
    # Calculate distance
    pulse_duration = time.ticks_diff(pulse_end, pulse_start)
    distance = (pulse_duration * 0.034) / 2  # Speed of sound conversion
    return distance

# **[ADDED BY AI - REVIEW]** - Northeastern campus distance measuring
led = Pin(25, Pin.OUT)  # Warning LED

print("Northeastern campus distance monitor")
while True:
    dist = measure_distance()
    print(f"Distance to object: {dist:.1f} cm")
    
    # Light LED if object too close (like approaching Matthews Arena)
    if dist < 20:
        led.on()
        print("Warning: Object very close!")
    else:
        led.off()
    
    time.sleep(0.5)
```

## Random Numbers [MAYBE]
```python
import random

# Generate random LED patterns
from machine import Pin
import time

leds = [Pin(i, Pin.OUT) for i in [15, 16, 17]]

while True:
    # Pick random LED
    led_index = random.randint(0, 2)
    leds[led_index].toggle()
    
    # Random delay
    delay = random.uniform(0.1, 1.0)
    time.sleep(delay)
```

---

# Communication Protocols [MAYBE]

## I2C Communication
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

## SPI Communication  
```python
from machine import Pin, SPI

# Create SPI object
spi = SPI(0, baudrate=1000000, polarity=0, phase=0, 
          sck=Pin(18), mosi=Pin(19), miso=Pin(16))

# Basic SPI operations (device-specific)
# spi.write(data)
# response = spi.read(num_bytes)
```

---

## **DEVELOPMENT GAPS COMPLETED:**

1. **[COMPLETED - REVIEW]** - Added complete servo motor examples with angle control function
2. **[COMPLETED - REVIEW]** - Added ultrasonic sensor (HC-SR04) distance measurement
3. **[COMPLETED - REVIEW]** - Enhanced analog sensor examples (photoresistor, thermistor) 
4. **[COMPLETED - REVIEW]** - Added serial communication/data logging for MATLAB integration
5. **[INSTRUCTOR REVIEW]** - Verify hardware pin assignments match your lab setups
6. **[STILL NEEDED]** - Pin assignment reference chart for Raspberry Pi Pico
7. **[STILL NEEDED]** - Common troubleshooting guide for hardware issues
8. **[STILL NEEDED]** - Power management concepts (if covered)

## **NOTES FOR COMPLETION:**
- Added Northeastern-themed examples throughout (campus buildings, weather, hockey themes)
- Focused on hardware you confirmed: buttons, LEDs, photoresistors, thermistors, servos, ultrasonic sensors
- Serial communication examples designed to work with MATLAB data import
- All added content marked with **[ADDED BY AI - REVIEW]** for easy identification