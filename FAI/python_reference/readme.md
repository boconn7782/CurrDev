# Python Reference Documentation
**Northeastern University First Year Engineering Program**

## Overview

This repository contains comprehensive Python and MicroPython reference materials specifically designed for Northeastern University's First Year Engineering courses. The documentation is structured to support both student learning and AI-assisted tutoring while maintaining clear boundaries around course scope and learning objectives.

## Documentation Structure

### 📋 [Coverage Index](python_coverage_index.md)
**Start here** - Master reference with all topic coverage levels and navigation links

### 📖 [Core Reference](python_reference_core.md) 
**Primary resource** - Essential Python concepts ([KNOW] and [HEARD] content) with examples and explanations

### 🔧 [MicroPython Extensions](micropython_extensions.md)
**Hardware programming** - Digital I/O, analog sensors, servos, and microcontroller-specific features

### ⚡ [Advanced Topics](python_maybe_advanced.md)
**Optional content** - Topics covered in some sections or pursued in individual projects ([MAYBE])

### ⛔ [Not Covered](python_not_covered.md)
**Scope boundaries** - Advanced concepts beyond course scope with redirection guidance ([NC])

## Coverage Level System

Our documentation uses a four-tier coverage system:

- **[KNOW]** - Students will know: Core concepts, emphasized and assessed
- **[HEARD]** - Students will have heard: Introduced for recognition, not assessed  
- **[MAYBE]** - Students may know: Section-specific or project-based learning
- **[NC]** - Not covered: Beyond scope, may impact assignment grades if used

## Educational Philosophy

### Procedural Programming Focus
All instruction emphasizes **procedural programming paradigms**. We avoid object-oriented patterns, class-based solutions, and advanced OOP concepts in introductory courses, saving these for upper-level coursework.

### Northeastern Context
Examples and applications are themed around Northeastern University, Boston, and engineering scenarios to increase student engagement and relevance.

## Hardware Coverage

### Core Hardware Topics (All Sections)
- Digital signals (buttons, LEDs)
- Analog signals (photoresistors, thermistors)  
- PWM (LED brightness control)
- Servo motor control
- Ultrasonic distance sensors
- Serial communication and monitoring

### Platform
- **Primary**: Raspberry Pi Pico with MicroPython
- **Integration**: MATLAB communication (some sections)

## Usage Guidelines

### For Students
1. Start with the [Coverage Index](python_coverage_index.md) to understand scope
2. Use [Core Reference](python_reference_core.md) for assignments and studying
3. Consult [MicroPython Extensions](micropython_extensions.md) for hardware projects
4. Check coverage levels before using advanced techniques

### For Instructors  
1. Reference [Coverage Index](python_coverage_index.md) for curriculum alignment
2. Use [Not Covered](python_not_covered.md) to redirect inappropriate questions
3. Customize [Advanced Topics](python_maybe_advanced.md) based on section needs
4. Update coverage levels as curriculum evolves

### For AI Assistant Integration
1. Primary reference: [Core Reference](python_reference_core.md)
2. Boundary enforcement: [Not Covered](python_not_covered.md)  
3. Scope checking: [Coverage Index](python_coverage_index.md)
4. Hardware support: [MicroPython Extensions](micropython_extensions.md)

## Content Development

### Version Control
- **Main branch**: Production-ready content for current semester
- **Development branches**: Content updates and curriculum changes
- **Release tags**: Semester-specific versions

### Content Guidelines
- All examples use Northeastern University themes
- Code examples are complete and tested
- Procedural programming approach enforced
- Clear coverage level indicators throughout

### Contributing
1. Review existing coverage levels before adding content
2. Mark new content with appropriate [KNOW/HEARD/MAYBE/NC] tags
3. Use Northeastern-themed examples where possible
4. Test all code examples on target hardware
5. Follow procedural programming guidelines

## Course Integration

### Supported Courses
- **ENGR 1201**: Cornerstone of Engineering 1
- **ENGR 1202**: Cornerstone of Engineering 2  
- **Related courses**: As specified by individual instructors

### Assessment Alignment
Content is specifically designed to support course assignments and avoid introducing concepts that could negatively impact student grades through inappropriate complexity.

### Cross-Platform Integration
- **MicroPython** ↔ **MATLAB** data exchange
- **Serial communication** protocols
- **File-based** data sharing methods

## Support Resources

### Documentation Maintenance
- Regular review of student questions and common issues
- Hardware troubleshooting guide (in development)
- Pin assignment reference (in development)
- Cross-reference links (pending final review)

### Additional Resources
- [Python Official Documentation](https://docs.python.org/3/)
- [MicroPython Documentation](https://docs.micropython.org/)
- [Raspberry Pi Pico Documentation](https://www.raspberrypi.org/documentation/microcontrollers/)

## Contact Information

**Course Development Team**  
Northeastern University First Year Engineering Program

**Technical Issues**  
Please report documentation errors or hardware issues through the course management system.

**Curriculum Questions**  
Contact your section instructor for course-specific guidance.

---

## Quick Navigation

| Topic | Coverage | Document |
|-------|----------|----------|
| Variables, Data Types | [KNOW] | [Core Reference](python_reference_core.md#variables-know) |
| Control Structures | [KNOW] | [Core Reference](python_reference_core.md#control-structures-know) |
| Functions | [KNOW] | [Core Reference](python_reference_core.md#functions-know) |
| Digital I/O | [KNOW] | [MicroPython Extensions](micropython_extensions.md#digital-io-with-pin-objects-know) |
| Analog Sensors | [KNOW] | [MicroPython Extensions](micropython_extensions.md#analog-operations-know) |
| List Comprehensions | [MAYBE] | [Advanced Topics](python_maybe_advanced.md#list-comprehensions) |
| Object-Oriented Programming | [NC] | [Not Covered](python_not_covered.md#object-oriented-programming-nc) |

---

*Last Updated: [Current Date]*  
*Version: 1.0*
