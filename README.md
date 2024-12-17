# Trackify: Smart Attendance and Engagement System  

**"Stay On Track, Stay Engaged!"**  

---

## Project Overview  
**Trackify** is an innovative **smart attendance system** designed to automate attendance tracking and optimize classroom engagement using **IoT hardware** and **AI-powered tools**. It addresses the limitations of traditional attendance systems by integrating **RFID authentication**, **Facial Recognition**, and **Ultrasonic Sensors** with a user-friendly dashboard and real-time notifications.

The system ensures:  
- Accurate attendance logging.  
- Energy-efficient classroom resource management.  
- Real-time analytics for students, professors, and administrators.  

---

## Table of Contents  
- [Key Features](#key-features)  
- [System Components](#system-components)  
- [System Architecture](#system-architecture)  
- [Installation Instructions](#installation-instructions)  
- [Usage](#usage)  
- [Project Structure](#project-structure)  
- [How It Works](#how-it-works)  
- [Demonstration](#demonstration)  
- [Future Enhancements](#future-enhancements)  
- [Contributors](#contributors)  
- [License](#license)  

---

## Key Features  

1. **Ultrasonic Proximity Detection**  
   - Detects individuals within a specified range (~50 cm) to activate the attendance system.  

2. **RFID Authentication**  
   - Provides a quick and secure check-in process for students and professors using RFID tags.  

3. **Facial Recognition**  
   - Secondary authentication method using OpenCV for face detection and recognition.  

4. **Classroom Resource Management**  
   - Automates **electrical resource control** (e.g., lights and power outlets) using a dual-relay card.  

5. **Real-Time Notifications**  
   - Sends pre-class reminders and attendance summaries via the **WhatsApp API**.  

6. **Data Storage and Visualization**  
   - Attendance and engagement data are stored in an **SQLite database** and displayed on intuitive dashboards.  

7. **User-Specific Dashboards**  
   - Tailored dashboards for administrators, professors, and students for data-driven decision-making.  

---

## System Components  

### Hardware  
- **Raspberry Pi 4**: Main processor handling all tasks.  
- **Ultrasonic Sensor (HC-SR04)**: Detects proximity to trigger the system.  
- **RFID Reader (MFRC522)**: Scans user RFID tags.  
- **Hikvision 1080p Camera**: Captures facial images for recognition.  
- **Dual-Relay Card**: Controls classroom electrical devices for energy efficiency.  

### Software  
- **Python**: Core programming language for hardware interaction and AI logic.  
- **OpenCV**: Library for facial detection and recognition.  
- **SQLite**: Lightweight database for attendance logs.  
- **WhatsApp API**: Sends real-time notifications.  
- **RPi.GPIO**: Controls GPIO pins on the Raspberry Pi.  

---

## System Architecture  

The system follows a **modular and scalable architecture**:  

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


---

## Installation Instructions  

### Prerequisites  
- **Raspberry Pi 4** (or similar single-board computer) with Raspbian OS installed.  
- **Python 3.x** installed.  
- Hardware components:  
  - RFID Reader (MFRC522)  
  - Ultrasonic Sensor (HC-SR04)  
  - Hikvision 1080p Camera  
  - Dual-Relay Card  

### Step 1: Clone the Repository  
Run the following command on your Raspberry Pi:
bash:
git clone https://github.com/your-repo-name/trackify.git
cd trackify

### Step 2: Install Dependencies
Install all required libraries using pip:
bash:
pip install opencv-python RPi.GPIO mfrc522 twilio sqlite3 matplotlib 

###Step 3: Connect Hardware Components

* Connect the ultrasonic sensor, RFID reader, and dual-relay card to the GPIO pins on the Raspberry Pi.
* Connect the Hikvision Camera to the Raspberry Pi via USB.

###Step 4: Run the System
Execute the main script:
bash:
python src/trackify_main.py


###Usage
####RFID Authentication
* Place your RFID tag on the reader.
* If verified, attendance is logged.
####Facial Recognition
* If RFID is unavailable, facial recognition is triggered.
* Look into the camera to confirm attendance.
####Classroom Resource Management
* Upon professor check-in, lights and power are activated.
* Resources are turned off automatically when the professor checks out.
####Notifications
* Students receive reminders 5 minutes before class via WhatsApp.
##Project Structure
Trackify/
├── src/
│   ├── trackify_main.py          # Main program logic
│   ├── rfid_reader.py            # Handles RFID scanning
│   ├── facial_recognition.py     # Facial recognition logic
│   ├── ultrasonic_sensor.py      # Proximity detection
│   ├── resource_manager.py       # Controls dual-relay card
├── database/
│   ├── attendance.db             # SQLite database for attendance
├── docs/
│   ├── architecture.png          # System architecture diagram
│   ├── hardware_setup.png        # Hardware connections
│   ├── dashboards/               # Dashboard screenshots
├── requirements.txt              # Required libraries
├── README.md                     # Documentation


##
Here is the code for the requested part with the updated section:

markdown
Copier le code
---

## Installation Instructions  

### Prerequisites  
- **Raspberry Pi 4** (or similar single-board computer) with Raspbian OS installed.  
- **Python 3.x** installed.  
- Hardware components:  
  - RFID Reader (MFRC522)  
  - Ultrasonic Sensor (HC-SR04)  
  - Hikvision 1080p Camera  
  - Dual-Relay Card  

### Step 1: Clone the Repository  
Run the following command on your Raspberry Pi:  
```bash
git clone https://github.com/your-repo-name/trackify.git
cd trackify
Step 2: Install Dependencies
Install all required libraries using pip:

bash
Copier le code
pip install opencv-python RPi.GPIO mfrc522 twilio sqlite3 matplotlib
Step 3: Connect Hardware Components
Connect the ultrasonic sensor, RFID reader, and dual-relay card to the GPIO pins on the Raspberry Pi.
Connect the Hikvision Camera to the Raspberry Pi via USB.
Step 4: Run the System
Execute the main script:

bash
Copier le code
python src/trackify_main.py
Usage
RFID Authentication
Place your RFID tag on the reader.
If verified, attendance is logged.
Facial Recognition
If RFID is unavailable, facial recognition is triggered.
Look into the camera to confirm attendance.
Classroom Resource Management
Upon professor check-in, lights and power are activated.
Resources are turned off automatically when the professor checks out.
Notifications
Students receive reminders 5 minutes before class via WhatsApp.
Project Structure
plaintext
Copier le code
Trackify/
├── src/
│   ├── trackify_main.py          # Main program logic
│   ├── rfid_reader.py            # Handles RFID scanning
│   ├── facial_recognition.py     # Facial recognition logic
│   ├── ultrasonic_sensor.py      # Proximity detection
│   ├── resource_manager.py       # Controls dual-relay card
├── database/
│   ├── attendance.db             # SQLite database for attendance
├── docs/
│   ├── architecture.png          # System architecture diagram
│   ├── hardware_setup.png        # Hardware connections
│   ├── dashboards/               # Dashboard screenshots
├── requirements.txt              # Required libraries
├── README.md                     # Documentation


#How It Works:
###System Activation: The ultrasonic sensor detects proximity and activates the system.
###RFID and Facial Recognition: Users scan their RFID tags or use facial recognition for attendance.
###Data Logging: Attendance data is stored in the SQLite database.
###Notifications: WhatsApp API sends class reminders and updates.
###Resource Control: Lights and power are managed to optimize energy usage.

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





