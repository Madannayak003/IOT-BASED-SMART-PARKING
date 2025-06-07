# IOT-BASED-SMART-PARKING
🚗 RFID Smart Parking System with Arduino UNO

Created by Madan R
Date: 18/05/2025

📋 Project Overview
This project is an RFID-based Smart Parking System using Arduino UNO. It integrates:

RFID (MFRC522) for user authentication,

IR sensors for slot occupancy detection,

Ultrasonic sensors for vehicle detection at entry and exit,

Servo motors for gate control,

ESP8266 for uploading data to the cloud (e.g., Google Sheets via Apps Script),

LEDs and Buzzer for feedback.

[Hardware Components]

Component	              Quantity	               Description
Arduino UNO	              1                  	Main controller
MFRC522 RFID	             1                  	For scanning RFID tags
Servo Motor	              2                   For entry and exit gates
HC-SR04	                  2                   Entry and exit vehicle detection
IR Sensors	               3                   For detecting slot availability
ESP8266 (e.g.,NodeMCU) 	  1	                  For cloud communication via SoftwareSerial
LEDs	                     2	                  Green (access granted), Red (denied)
Buzzer	                   1	                  Sound alert for denial
Power Supply              1                	  5V regulated power supply


[Pin Configuration]
 
Purpose	                             Pin
RFID SS (SDA)                        D10
RFID RST	                            D9
IR Sensor Slot 1	                    A0
IR Sensor Slot 2	                    A1
IR Sensor Slot 3                    	A2
Red LED + Buzzer                    	A3
Green LED                            D2
Entry Ultrasonic Trig	               D7
Entry Ultrasonic Echo            	   D8
Exit Ultrasonic Trig	                D4
Exit Ultrasonic Echo	                D3
Entry Servo                      	   D5
Exit Servo	                          D6
ESP8266 RX, TX	                      A4 (RX), A5 (TX) – SoftwareSerial

[How It Works]

1. RFID Scan: When a vehicle is at the gate, the driver scans their RFID card.

2. Validation: UID is checked against a list of authorized cards.

3. Vehicle Detection:

     If at Entry and authorized → check if slots are available.

     If at Exit and authorized → verify if UID was previously registered (i.e., the car entered).

4. Slot Assignment: An available slot (via IR sensors) is assigned.

5. Gate Control: Gates are opened/closed using servo motors.

6. ESP Communication: Status (ENTRY or EXIT), UID, available slots, and assigned slot are sent to ESP8266 via SoftwareSerial.

7. Feedback: LEDs and buzzer indicate success/failure visually and audibly.

[##Notes]
Distance for car detection: < 5cm from the ultrasonic sensor.

Empty slot logic: IR sensor returns HIGH when the slot is empty.

Gate movement: Smooth 0° ↔ 90° transition using servo.

##Setup Instructions
 
Connect all components as per the pin configuration.

Replace validUIDs[] with your RFID card UIDs.

Upload the code to the Arduino UNO.

Power the system and monitor the Serial output.


[Installation]

Upload Arduino Code (arduino_parking.ino)

Handles RFID, servo gates, IR/ultrasonic detection

Sends data to ESP8266 via Serial: ENTRY:UID:slots:slotno or EXIT:UID:slots:-

Upload ESP8266 Code (esp_parking.ino)

Receives Serial data from Arduino

Sends HTTP request to Google Apps Script Web App

Google Apps Script (Final-Parking)

Logs data to Google Sheet

Sends Gmail with PDF (Ticket/Receipt)

Logs feedback responses

Google Sheets Setup

Log Sheet ID: 1ofg-9cGfbXVbg6lBfyV7j*****************

Feedback Sheet ID: 14PausWOSExNV0K8o*****************

Sheet Names: Logs, Feedback, etc.


Email Output
Entry Email:

PDF Ticket with UID, Entry Time, Slot,

"Welcome" message

Exit Email:

PDF Receipt with UID, Entry Time, Exit Time, Duration, Charge (Rs. 50/10 min) UPI QR code 

![image alt](https://github.com/Madannayak003/IOT-BASED-SMART-PARKING/blob/36fd43a7e48c4cca31b172fe9532ad7bb446c744/entry-exit-ticket.jpeg)

Thank you Email with feedback and payment confirm:

![image alt](https://github.com/Madannayak003/IOT-BASED-SMART-PARKING/blob/ce9e93f16c22ae97b4e38d72159a03016cac4adb/thank%20you%20mail.jpeg)

feedback form :

![image alt](https://github.com/Madannayak003/IOT-BASED-SMART-PARKING/blob/36fd43a7e48c4cca31b172fe9532ad7bb446c744/feedback-form.jpeg)

project image:

![image alt](https://github.com/Madannayak003/IOT-BASED-SMART-PARKING/blob/36fd43a7e48c4cca31b172fe9532ad7bb446c744/project-structure.jpeg)

📽️ Watch Demo Video:

[![Watch Video](https://img.icons8.com/color/96/youtube-play.png)](https://drive.google.com/file/d/10fCxwIr7GQCxG0gdvVvFNceyp6BNLXks/view?usp=drive_link)

for knowing RFID CARD UID use this : https://github.com/Madannayak003/RFID_UID-ARDUINO

MIT License © 2025 Madan R

## 🌐 Website
[![Netlify Status](https://img.shields.io/badge/Live%20Site-Netlify-brightgreen?style=for-the-badge&logo=netlify)](https://stellular-genie-403aa8.netlify.app)
