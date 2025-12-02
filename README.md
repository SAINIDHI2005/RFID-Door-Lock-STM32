**🔐 RFID-Based Door Lock System using STM32 Nucleo F446RE**

This project implements a simple RFID-based access control system using the STM32 Nucleo-F446RE, RC522 RFID reader, 16×2 LCD display, and an SG90 servo motor. The entire prototype is built on a breadboard and uses SPI, PWM, and GPIO peripherals available on the STM32.
The system continuously scans for RFID cards, verifies them, and controls a servo-based door lock mechanism based on authentication results.
________________________________________
**📦 Hardware Used**

•	STM32 Nucleo-F446RE

•	RC522 RFID Reader (MFRC522)

•	SG90 Servo Motor

•	16×2 LCD (4-bit mode)

•	Breadboard, jumper wires, power supply
________________________________________
**⚙️ How the System Works**
1.	The MFRC522 RFID module is initialized over SPI.
2.	Inside the main loop, the RFID status is polled continuously using:
o	MFRC522_Request()
o	MFRC522_Anticoll()
3.	When an RFID tag or card is detected:
o	The card UID is read.
o	UID is compared against a list of allowed UIDs.
4.	Based on authentication:
o	Valid UID
	LCD displays ACCESS GRANTED for 3 seconds
	Servo rotates from 0° to 180° (unlock position)
	After 3 seconds, LCD shows DOOR LOCKED
	Servo rotates back to 0° (locked position)
o	Invalid UID
	LCD displays ACCESS DENIED for 3 seconds
	LCD then returns to DOOR LOCKED
________________________________________
**🧰 Software & Libraries**

This project uses:

•	STM32 HAL drivers

•	RC522.h and related driver files

•	lcd.h and LCD driver

•	Standard C libraries (string.h, stdint.h, etc.)

PWM is generated using TIM2–Channel 1 for controlling the servo. LCD is operated in 4-bit mode using GPIO pins. UART (USART2) is optionally used for debugging UID values of RFID tags or cards.

