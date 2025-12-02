# 🔐 RFID-Based Door Lock System using STM32 Nucleo F446RE

This project demonstrates a basic access-control mechanism where a door lock is controlled through RFID-based authentication. The system continuously monitors for RFID tags, verifies them against predefined UIDs, and provides visual feedback along with a servo-driven lock action. It serves as a simple prototype for electronic door security systems, combining microcontroller programming with real-time interfacing.

---

## 📦 Hardware Used
- STM32 Nucleo-F446RE  
- RC522 RFID Reader (MFRC522) 
- SG90 Servo Motor  
- 16×2 LCD (4-bit mode)  
- Breadboard, jumper wires, power supply
- 4x AA Batteries and Holder

---

## ⚡ Circuit Diagram
![image alt](https://github.com/SAINIDHI2005/RFID-Door-Lock-STM32/blob/22d4cd7346636bf5ae76a9dedb5d1f38536748ef/Screenshot%202025-12-02%20151008.png)

---

## ⚙️ How the System Works

1. The MFRC522 RFID module is initialized over SPI.  
2. Inside the main loop, the RFID status is polled continuously using:
   - `MFRC522_Request()`
   - `MFRC522_Anticoll()`
3. When an RFID tag or card is detected:
   - The card UID is read.
   - UID is compared against a list of allowed UIDs.
4. Based on authentication:

### ✅ Valid UID
- LCD displays **ACCESS GRANTED** for 3 seconds  
- Servo rotates from **0° to 180°** (unlock position)  
- After 3 seconds, LCD shows **DOOR LOCKED**  
- Servo rotates back to **0°** (locked position)  

### ❌ Invalid UID
- LCD displays **ACCESS DENIED** for 3 seconds  
- LCD then returns to **DOOR LOCKED**

---

## 🧰 Software & Libraries

This project uses:

- **STM32CubeIDE** (project creation, building, debugging)  
- STM32 HAL drivers  
- `RC522.h` and related driver files  
- `lcd.h` and LCD driver  
- Standard C libraries (`string.h`, `stdint.h`, etc.)

IOC File window:

![image alt](https://github.com/SAINIDHI2005/RFID-Door-Lock-STM32/blob/4602fcf86b4680c012bfa067356dff780c6f18f2/Screenshot%202025-12-02%20150650.png)

Additional details:

- PWM is generated using **TIM2–Channel 1** for controlling the servo.  
- LCD is operated in **4-bit mode** using GPIO pins.  
- UART (USART2) is optionally used for debugging UID values.

---

## Project Image:
![image alt](https://github.com/SAINIDHI2005/RFID-Door-Lock-STM32/blob/0832ed2848aec3c5fa4ea1a3ff2479425d09ca23/WhatsApp%20Image%202025-12-02%20at%2015.21.28_5ea8f595.jpg)
