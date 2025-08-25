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
- **Character Alignment**: Maintain exactly 30 characters before each `│` symbol to ensure consistent vertical alignment. This can be exceeded if component names are long, but use standard abbreviations to minimize this.

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

### 4. Parallel Component Standards
- **Placement**: Always place parallel components (resistors, capacitors, etc.) immediately below the main connection line (on the very next line before proceeding to the next row of PICO connections)
- **Left Side Format**: Use `connection <-- component -┘` for components on the left side, preceeded by connection (e.g., `GND <-- 10kΩ -┘`)
- **Right Side Format**: Use `└- component --> connection` for components on the right side, followed by connection (e.g., `└- 10kΩ --> GND`)
- **Multiple Components**: Each parallel component gets its own line with consistent indentation
- **Layout Priority**: Circuit clarity takes precedence over maintaining perfect Pico outline - breaks in the frame are acceptable for clear parallel component representation

### 5. Power and Ground Conventions
- **Power Rail**: Always connect to `3V3(OUT)` pin 36
- **GND Rail**: Can connect to any GND pin (3, 8, 13, 18, 23, 28, 38)
- **Notation**: Use "Power Rail" and "GND Rail" terminology consistently

### 6. Reference Designator Standards
- **Standard Industry Designators**: Use proper electronic component reference designators
  - LEDs: D1, D2, D3...
  - Resistors/Potentiometers: R1, R2, R3...
  - Motors/Servos: M1, M2, M3...
  - Switches/Buttons: SW1, SW2, SW3...
  - Sensors: U1, U2, U3... (or specific like LDR1 for photoresistors)
- **Pin Naming**: Use underscore format: `D1_R`, `R1_2`, `M1_1`
- **Descriptive Labels**: Include functional descriptions with designators when space allows

## Response Format Standards

### 1. Component List (First Section)
Always begin responses with a component confirmation list:

```markdown
## Component List

To clarify, are these the components you are working with and their pin configurations, correct?

* Component Type (Reference Designator) - Pin Count component (special notes)
   * REF_PIN - Pin Description
   * REF_PIN - Pin Description
```

**Example:**
```markdown
* RGB LED (D1) - 4-Pin component (common cathode)
   * D1_R - Red Anode
   * D1_G - Green Anode
   * D1_B - Blue Anode
   * D1_GND - Common Cathode (GND)
* Servo Motor (M1) - 3-Pin component
   * M1_1 - Signal
   * M1_2 - GND
   * M1_3 - Power
```

### 2. ASCII Wiring Diagram (Second Section)
- Use reference designators and descriptors in the diagram
- Follow all alignment and parallel component rules
- Include disclaimer: `*Note: This ASCII diagram shows basic connections - see Component Connections below for complete wiring details*`

### 3. Component Connections Section (Third Section)
- Use reference designators and descriptive labels consistently
- Group by component categories (LEDs, Sensors, Actuators, etc.)
- Include all passive components (resistors, capacitors) with values
- Specify power requirements and communication protocols

### 4. Code Pin Definitions (Fourth Section)
- Use descriptive, uppercase constants
- Group related pins together
- Follow functional naming conventions

## Component Connection Section Standards

### Layout Format
```markdown
## Component Connections

### Category Name (with specifications)
- **Component Name (Reference Designator)**: 
  - REF_PIN Description → GPIO Pin
  - REF_PIN Description → Rail/Component
```

### Component Categories (in order of appearance)
1. **LEDs** (include current limiting resistor values)
2. **Buttons/Switches** (include pull-up/pull-down resistor info)  
3. **Sensors** (include power requirements and communication protocol)
4. **Actuators** (motors, servos, etc.)
5. **Communication Devices** (LCD, OLED, etc.)
6. **Power Components** (voltage regulators, etc.)

### Required Information for Each Component
- **Pin mappings**: Specific GPIO connections using reference designators
- **Power connections**: Voltage requirements and rail connections
- **Passive components**: Resistor values with clear connections to GND/Power
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

## Best Practices for Instructors

### When Creating Diagrams
1. **Start with component confirmation**: Always begin with the component list for verification
2. **Use reference designators consistently**: Apply throughout all sections
3. **Prioritize clarity over aesthetics**: Break Pico frame if needed for parallel component clarity
4. **Verify pin capabilities**: Ensure ADC pins are used for analog, PWM-capable pins for servos
5. **Check power requirements**: Confirm 3.3V compatibility for all components

### When Reviewing Student Work
1. **Check component identification**: Verify proper reference designators are used
2. **Validate pin assignments**: Ensure appropriate pin types are used
3. **Review parallel components**: Check resistor placements and values
4. **Test code compatibility**: Ensure pin definitions match physical connections

### Common Issues to Watch For
- **Voltage mismatches**: 5V components on 3.3V pins
- **Current overload**: Too many LEDs without current limiting
- **Pin conflicts**: Multiple functions assigned to same GPIO
- **Missing pull resistors**: Floating inputs on buttons/switches
- **Inconsistent reference designators**: Mixed naming conventions
- **Unclear parallel connections**: Missing or misplaced passive components

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
1. Begin with component confirmation list using proper reference designators
2. Apply all formatting standards from this guide including 30-character alignment
3. Use parallel component notation for all passive components
4. Include complete Component Connections section with reference designators
5. Provide matching Code Pin Definitions
6. Verify pin assignments follow best practices
7. Prioritize circuit understanding over diagram aesthetics
