# SE20UARI146_SE20UARI141_SE20UARI025

# Motion Sensing with Raspberry Pi

## Overview

This repository contains Python code for interfacing a Passive Infrared (PIR) motion sensor with a Raspberry Pi. The code detects motion using the PIR sensor and prints a message when motion is detected.

## Passive Infrared (PIR) Motion Sensor

The Passive Infrared (PIR) motion sensor is a widely used sensor for detecting motion. It operates based on the principle of detecting changes in the infrared radiation emitted by objects as they move within its detection range. PIR sensors are commonly used in security systems, lighting control, and other applications where motion detection is required.

## Components

To set up this project, you will need the following components:

- *Raspberry Pi*: Any Raspberry Pi model with GPIO pins will work.

- *Passive Infrared (PIR) Motion Sensor*: The PIR sensor is a common motion detection sensor that works by detecting changes in the infrared radiation emitted by objects as they move within its detection range.

- *Jumper Wires*: To connect the PIR sensor to the Raspberry Pi.

### Wiring

Connect the PIR sensor to the Raspberry Pi as follows:

- *PIR VCC (Power)*: Connect this pin to the Raspberry Pi's 5V pin.

- *PIR GND (Ground)*: Connect this pin to the Raspberry Pi's Ground (GND) pin.

- *PIR OUT (Signal)*: Connect this pin to a GPIO pin on the Raspberry Pi (e.g., GPIO pin 16).

## Code Explanation

The Python code in this repository interfaces with the Raspberry Pi's GPIO pins to detect motion using the PIR sensor. Here's a detailed explanation of the code:

1. *Import the Necessary Libraries*:
   - `import RPi.GPIO as GPIO`: This imports the Raspberry Pi GPIO library, enabling control over the GPIO pins.
   - `import time`: The `time` module is used to create time delays in the script.

2. *Define the GPIO Pin for the PIR Sensor*:
   - `pir_sensor_pin = 16`: Set the `pir_sensor_pin` variable to the GPIO pin number where the PIR sensor is connected. Modify this to match your physical setup.

3. *Set Up GPIO Mode and Pin as an Input*:
   - `GPIO.setmode(GPIO.BOARD)`: Configure the GPIO mode to BOARD mode, which uses the physical pin numbering scheme on the Raspberry Pi. Alternatively, you can use `GPIO.setmode(GPIO.BCM)` to use the Broadcom SOC channel numbering scheme.
   - `GPIO.setup(pir_sensor_pin, GPIO.IN)`: Configure the specified GPIO pin (`pir_sensor_pin`) as an input pin to read the PIR sensor's output.

4. *Enter a Try-Except-Finally Block*:
   - The try block contains the main code for detecting motion using the PIR sensor.

5. *Inside the While Loop* (`while True`):
   - `motion_detected = GPIO.input(pir_sensor_pin)`: Read the current state of the GPIO pin connected to the PIR sensor. If motion is detected, this pin will go high (1), setting `motion_detected` to `True`. If no motion is detected, it will be `False`.
   - `if motion_detected: print("Motion detected!")`: Check if motion is detected (i.e., `motion_detected` is `True`). If motion is detected, print "Motion detected!" to the console.
   - `time.sleep(0.1)`: Add a short delay of 0.1 seconds between each iteration of the loop to prevent rapid polling of the sensor.

6. *Exception Handling*:
   - The code includes an exception handler for KeyboardInterrupt (Ctrl+C) to stop the program gracefully.

7. *Finally Block*:
   - `GPIO.cleanup()`: This function is called to release and clean up the GPIO pins. It ensures that the GPIO pins are reset to their default state when the program exits.

## Running the Code

To use this code with your Raspberry Pi and PIR sensor, follow these steps:

1. Ensure that the PIR sensor is wired correctly to the Raspberry Pi as described in the "Wiring" section.

2. Clone this repository to your Raspberry Pi or transfer the code file (`pir_motion_sensor.py`) to your Raspberry Pi.

3. Open a terminal and navigate to the directory containing the code.

4. Run the code using the command: `python pir_motion_sensor.py`

5. The program will continuously monitor the PIR sensor. When motion is detected, it will print "Motion detected!" to the console.

6. To stop the program, press Ctrl+C in the terminal.

## Customization

- You can change the GPIO pin used by modifying the `pir_sensor_pin` variable in the code to match your physical setup.

- Adjust the sleep duration (`time.sleep(0.1)`) to change the polling frequency of the PIR sensor.
