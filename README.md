# Simple-Door-Lock-STM32
A simple yet robust door lock controller project using the STM32 microcontroller, L293D motor driver, and a 12V automotive central locking actuator. It supports open/close control via external buttons, with debounced interrupt handling and latched LED light control based on the door state.

🔧 Features
🧠 Interrupt-driven door open/close control (via EXTI)
🔄 Uses L293D H-Bridge driver to operate 12V actuator
🔒 Latching light indication system to reflect lock state
🧹 Debounce logic to prevent false triggering
🚫 Ignores conflicting inputs (open & close pressed together)
🕹️ Manual control using physical push buttons

⚙️ Hardware Used
Component	Description
STM32F103C8T6 / F401	ARM Cortex-M MCU
L293D	Dual H-Bridge Motor Driver (12V rated)
12V Actuator Motor	Car central locking motor
Push Buttons	For Open / Close control (w/ pull-down)
LEDs	Status indicators (locked / unlocked state)
Power Supply	12V source for actuator + 3.3V for logic

📦 Pin Mapping
GPIO Pin	Function
PA10	Motor IN1 (Open)
PA11	Motor IN2 (Close)
PA8	LED 1 (Light Indicator)
PA9	LED 2 (Light Indicator)
PB4	Open Button (Interrupt)
PB5	Close Button (Interrupt)

🧠 Software Logic
When Open button is pressed:
PA10 = HIGH, PA11 = LOW (motor opens door)
Light = ON (PA9 = HIGH)
Motor stops after delay
When Close button is pressed:
PA10 = LOW, PA11 = HIGH (motor closes door)
Light = OFF
Both pressed → ignored to prevent conflicting commands
Debouncing uses HAL_GetTick() and 100ms threshold

![Central Lock System]([https://your-image-link.com/image.jpg](https://github.com/BinethGeesara/Simple-Door-Lock-STM32/blob/0102b721df1a17994dd59f6b575486e6d443e427/IMG_4228.jpg))
