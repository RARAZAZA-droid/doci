# API.C - Embedded System API Layer

## Overview
This file contains the API layer implementation for an embedded system with multiple sensor and actuator functionalities including object detection, distance measurement, light source detection, and script execution.

## Main Functions

### 1. `object_detector()`
Implements a finite state machine for object detection using ultrasonic sensor and servo motor scanning from 0° to 180°.

### 2. `telemeter()`
Provides distance measurement functionality with servo positioning - receives angle input, moves servo, and continuously measures/sends distance data.

### 3. `light_detector()`
Implements light source detection using LDR sensors with calibration and scanning capabilities.

### 4. `light_object_detector()`
Combined functionality for detecting both light sources and objects simultaneously.

### 5. `script_fsm()`
Comprehensive script management system with file upload and playback capabilities for 10 different scripts.

## Helper Functions

### Servo Control
- `move_servo(int angle)`: Moves servo directly to specified angle
- `servo_scan(int angle1, int angle2, int flag)`: Continuous scanning between angles

### Sensor Functions
- `measure_distance()`: Measures distance using ultrasonic sensor (0-400 cm)
- `servo_deg(int p)`: Points servo and displays angle/distance on LCD
- `meas_and_send_distance()`: Measures and sends distance data to PC
- `meas_and_send_ldr()`: Measures light from both LDR sensors
- `calc_and_send_angle(int p)`: Sends angle data to PC
- `LDR(int LDR_index)`: Samples light intensity from specified LDR

### Script Management
- `read_txt(int script_num)`: Reads and displays text scripts on LCD
- `play_script(int script_num)`: Executes scripts with various opcodes (1-8)
- `addFile(const char * filename, int fileSize)`: Adds file to manager

### LCD Display
- `inc_lcd(int x)`: Counts up from 0 to x
- `dec_lcd(int x)`: Counts down from x to 0
- `rra_lcd(int x)`: Right rotation animation
- `set_delay(int delay)`: Sets delay time for animations

### Flash Memory
- `flash_write(int script_num, int write_flag_up)`: Writes script to flash
- `flash_write_calib(int ldr_value, int addr)`: Writes calibration data
- `send_calib_arr()`: Reads and sends calibration array

## Hardware Components
- Servo Motor, Ultrasonic Sensor, LDR Sensors, LCD Display, Flash Memory, ADC, Timers

## Dependencies
- api.h, stdio.h, string.h, stdlib.h