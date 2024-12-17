# Trackify: Smart Attendance and Engagement System  

**_"Stay On Track, Stay Engaged!"_**  

---

## Project Overview  

**Trackify** is an innovative **smart attendance system** designed to automate attendance tracking and optimize classroom engagement using **IoT hardware** and **AI-powered tools**.  

It addresses the limitations of traditional attendance systems by integrating:  
- **RFID authentication**  
- **Facial Recognition**  
- **Ultrasonic Sensors**  

This system ensures:  
- ✅ Accurate attendance logging  
- ✅ Energy-efficient classroom resource management  
- ✅ Real-time analytics for students, professors, and administrators  

---

## Table of Contents  

1. [Key Features](#key-features)  
2. [System Components](#system-components)  
3. [System Architecture](#system-architecture)  
4. [Installation Instructions](#installation-instructions)  
5. [Usage](#usage)
6. [Future Enhancements](#future-enhancements)  
7. [Contributors](#contributors)  
8. [License](#license)  
9. [Project Structure](#project-structure)  

---

## Key Features  

- 🚀 **Ultrasonic Proximity Detection**  
   - Detects individuals within a range of ~50 cm to activate the system.  

- 🔐 **RFID Authentication**  
   - Provides quick and secure check-in for students and professors.  

- 🧠 **Facial Recognition**  
   - Secondary authentication using OpenCV-based face detection.  

- 💡 **Classroom Resource Management**  
   - Automates control of lights and power using a dual-relay card.  

- 📱 **Real-Time Notifications**  
   - Sends pre-class reminders and attendance summaries via WhatsApp API.  

- 📊 **Data Storage and Visualization**  
   - Logs attendance in an **SQLite database** and provides intuitive dashboards.  

- 🎯 **User-Specific Dashboards**  
   - Custom dashboards for administrators, professors, and students.  

---

## System Components  

### 🛠 Hardware  

- **Raspberry Pi 4**: Main processing unit  
- **Ultrasonic Sensor (HC-SR04)**: Proximity detection  
- **RFID Reader (MFRC522)**: Scans user RFID tags  
- **Hikvision 1080p Camera**: Captures images for facial recognition  
- **Dual-Relay Card**: Manages classroom electrical devices  

### 💻 Software  

- **Python**: Core programming language  
- **OpenCV**: Facial recognition library  
- **SQLite**: Database for attendance logs  
- **WhatsApp API**: Sends notifications  
- **RPi.GPIO**: Manages GPIO pins on Raspberry Pi  

---
## Future Enhancements  

1. **Mobile App Integration**: Access attendance records via mobile apps.  
2. **Cloud Integration**: Migrate data to a cloud-based database for scalability.  
3. **Emotion Detection**: Assess student engagement using facial expression analysis.  
4. **Energy Optimization**: Enhance IoT controls for resource management.  

---

## Contributors  

- **Ahmed Rekik**  
- **Wael Baccouche**  
- **Nabil Chelly**  
- **Skander Amira**  
- **Younes Farah**  

---

## License  

This project is licensed under the **MIT License**.  

---

This is clean and perfectly formatted with proper headings, code blocks, and markdown styling. Let me know if you need further adjustments! 🚀

## System Architecture  

```plaintext
+--------------------+          +-------------------+          +----------------------+
|   Ultrasonic       |          |     RFID Reader   |          |    Camera Module     |
|    Sensor          |          |    (MFRC522)      |          |   (Hikvision 1080p)  |
+--------------------+          +-------------------+          +----------------------+
          |                                |                               |
          |                                |                               |
          +-------------+------------------+---------------+---------------+
                        | Raspberry Pi 4 (Central Hub)      |
                        +-----------------------------------+
                        |  Facial Recognition (OpenCV)      |
                        |  Data Processing (Python)         |
                        |  Attendance Logs (SQLite)         |
                        |  WhatsApp API Notifications       |
                        +-----------------------------------+
                                  |
                                  v
                        +------------------------+
                        | Dashboards (Admin UI)  |
                        | User Management        |
                        | Attendance Analytics   |
                        +------------------------+


