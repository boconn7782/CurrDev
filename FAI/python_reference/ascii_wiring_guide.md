# ASCII Wiring Diagram Standards for Raspberry Pi Pico

## Overview
This document establishes consistent formatting standards for creating ASCII-based wiring diagrams for Raspberry Pi Pico projects. These diagrams provide quick visual reference for pin connections without requiring external graphics software.

## Baseline Pi Pico Pinout Template

### Standard Pinout Reference
```
                              ┌─────[USB]─────┐
                          GP0 │●1          40●│ VBUS
                          GP1 │●2          39●│ VSYS  
                          GND │●3          38●│ GND
                          GP2 │●4          37●│ 3V3(EN)
                          GP3 │●5          36●│ 3V3(OUT)
                          GP4 │●6          35●│ ADC_VREF
                          GP5 │●7          34●│ GP28 (ADC2)
                          GND │●8          33●│ GND
                          GP6 │●9          32●│ GP27 (ADC1)
                          GP7 │●10         31●│ GP26 (ADC0)
                          GP8 │●11         30●│ RUN
                          GP9 │●12         29●│ GP22
                          GND │●13         28●│ GND
                         GP10 │●14         27●│ GP21
                         GP11 │●15         26●│ GP20
                         GP12 │●16         25●│ GP19
                         GP13 │●17         24●│ GP18
                          GND │●18         23●│ GND
                         GP14 │●19         22●│ GP17
                         GP15 │●20         21●│ GP16
                              └───────────────┘
```

## ASCII Wiring Diagram Rules

### 1. Pin Layout Standards
- **GPIO Labels**: Always place outside the frame (left or right side)
- **Pin Numbers**: Always inside the frame with bullet point (●)
- **Special Pins**: Include functional labels in parentheses when relevant
  - Example: `GP28 (ADC2)`, `3V3(OUT)`

### 2. Connection Arrow Standards
- **Connected Pins**: Use arrows (`---->` or `<----`) to show connections
- **Unconnected Pins**: No arrows, just the pin label and number
- **Arrow Direction**: 
  - `---->` for outputs from Pico (e.g., LED control)
  - `<----` for inputs to Pico (e.g., sensor readings, button presses)
  - Power connections can use either direction for clarity

### 3. Component Connection Format
```
    Component Pin  ----> GPIO_PIN │●NN         NN●│ GPIO_PIN <---- Component Pin 
                         GPIO_PIN │●NN         NN●│ GPIO_PIN <---- Component Pin 
    Component Pin  ----> GPIO_PIN │●NN         NN●│ GPIO_PIN                     
```

### 4. Power and Ground Conventions
- **Power Rail**: Always connect to `3V3(OUT)` pin 36
- **GND Rail**: Can connect to any GND pin (3, 8, 13, 18, 23, 28, 38)
- **Notation**: Use "Power Rail" and "GND Rail" terminology consistently

## Component Connections Section Standards

### Layout Format
```markdown
## Component Connections

### Category Name (with specifications)
- **Component Name**: Specific Pin → GPIO Pin, Additional info
- **RGB LED**: 
  - Red Anode → GP3
  - Green Anode → GP4
  - Blue Anode → GP5
  - Common Cathode → GND Rail
- **LCD with I2C**: VCC → Power Rail, GND → GND Rail, SDA → GP6, SCL → GP7
```

### Component Categories (in order of appearance)
1. **LEDs** (include current limiting resistor values)
2. **Buttons/Switches** (include pull-up/pull-down resistor info)  
3. **Sensors** (include power requirements and communication protocol)
4. **Actuators** (motors, servos, etc.)
5. **Communication Devices** (LCD, OLED, etc.)
6. **Power Components** (voltage regulators, etc.)

### Required Information for Each Component
- **Pin mappings**: Specific GPIO connections
- **Power connections**: Voltage requirements and rail connections
- **Passive components**: Resistor values, capacitor specs when relevant
- **Communication protocols**: I2C addresses, SPI settings, UART baud rates
- **Special notes**: Voltage levels, current draw, timing considerations

## Code Pin Definitions Standards

### Format and Organization
```python
# Comment describing pin category
PIN_NAME = gpio_number
COMPONENT_FUNCTION = gpio_number

# Group related pins together
# Use descriptive, uppercase constants
# Follow functional naming convention
```

### Naming Conventions
- **LEDs**: `LED_COLOR` or `LED1_RED`, `LED2_GREEN`
- **Buttons**: `BUTTON1`, `BTN_START`, `SW_MODE`
- **Sensors**: `SENSOR_TYPE` or `TEMP_SENSOR`, `LIGHT_SENSOR`
- **Communication**: `I2C_SDA`, `I2C_SCL`, `UART_TX`, `UART_RX`
- **PWM**: `PWM_SERVO`, `PWM_MOTOR`
- **ADC**: `ADC_POT`, `ADC_VOLTAGE`

### Pin Definition Categories (in order)
1. **Digital Output Pins** (LEDs, relays, etc.)
2. **Digital Input Pins** (buttons, switches, etc.)
3. **PWM Pins** (servos, motors, etc.)
4. **ADC Pins** (analog sensors, potentiometers)
5. **Communication Pins** (I2C, SPI, UART)
6. **Special Function Pins** (interrupts, timers)

### Example Code Pin Definitions
```python
# LED control pins
LED1_RED = 0
LED2_GREEN = 1
LED3_BLUE = 2

# RGB LED pins
RGB_RED = 3
RGB_GREEN = 4  
RGB_BLUE = 5

# Button input pins
BUTTON1 = 10
BUTTON2 = 11

# I2C communication
I2C_SDA = 6
I2C_SCL = 7

# ADC inputs
POT_ADC = 28
LIGHT_SENSOR_ADC = 27
```

## Best Practices for Instructors

### When Creating Diagrams
1. **Start with the template**: Always begin with the baseline pinout
2. **Add connections systematically**: Work from left to right, top to bottom
3. **Group related components**: Place similar functions near each other
4. **Verify pin capabilities**: Ensure ADC pins are used for analog, PWM-capable pins for servos
5. **Check power requirements**: Confirm 3.3V compatibility for all components

### When Reviewing Student Work
1. **Check pin assignments**: Verify appropriate pin types are used
2. **Validate power connections**: Ensure proper voltage levels
3. **Review component values**: Check resistor calculations and component ratings
4. **Test code compatibility**: Ensure pin definitions match physical connections

### Common Issues to Watch For
- **Voltage mismatches**: 5V components on 3.3V pins
- **Current overload**: Too many LEDs without current limiting
- **Pin conflicts**: Multiple functions assigned to same GPIO
- **Missing pull resistors**: Floating inputs on buttons/switches
- **Power distribution**: Inadequate ground connections

## Template Usage

### What Templates Mean
"Template files" refers to **instructions for the AI assistant** to generate common circuit diagram formats when requested. These are not separate files but rather standardized patterns the assistant should follow.

### Template Categories
When students or instructors request help with circuits, the assistant should offer to generate diagrams using these standardized formats:

**Simple Circuit Template (1-3 components)**
- Basic LED + button combinations
- Single sensor readings
- Simple actuator control

**Medium Circuit Template (4-7 components)**  
- Multiple LEDs with sensors
- LCD display with inputs
- Motor control with feedback

**Complex Circuit Template (8+ components)**
- Multi-sensor data logging
- Interactive display systems
- Comprehensive control panels

**Communication-Heavy Template**
- Multiple I2C devices
- SPI sensor networks  
- UART data transmission

### Usage Instructions
When generating any circuit diagram, the assistant should:
1. Select the appropriate template complexity
2. Apply all formatting standards from this guide
3. Include complete Component Connections section
4. Provide matching Code Pin Definitions
5. Verify pin assignments follow best practices