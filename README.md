# Import necessary libraries
import RPi.GPIO as GPIO
from mfrc522 import SimpleMFRC522
import cv2
import time

# Constants for GPIO pins
ULTRASONIC_TRIG = 23
ULTRASONIC_ECHO = 24

# Authorized users
AUTHORIZED_TEACHERS = ['123456789', '987654321', '462945141832']
AUTHORIZED_STUDENTS = ['2233445566']

# RFID Reader setup
reader = SimpleMFRC522()

# Initialize GPIO
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)
GPIO.setup(ULTRASONIC_TRIG, GPIO.OUT)
GPIO.setup(ULTRASONIC_ECHO, GPIO.IN)

# Function to check proximity using ultrasonic sensor
def check_ultrasonic():
    GPIO.output(ULTRASONIC_TRIG, True)
    time.sleep(0.00001)
    GPIO.output(ULTRASONIC_TRIG, False)

    start_time = time.time()
    stop_time = time.time()

    # Save StartTime
    while GPIO.input(ULTRASONIC_ECHO) == 0:
        start_time = time.time()

    # Save time of arrival
    while GPIO.input(ULTRASONIC_ECHO) == 1:
        stop_time = time.time()

    # Calculate distance
    time_elapsed = stop_time - start_time
    distance = (time_elapsed * 34300) / 2
    return distance

# Function for RFID authentication
def rfid_authentication():
    try:
        print("Waiting for RFID card...")
        id, text = reader.read()
        print(f"Card scanned with UID: {id}")
        if str(id) in AUTHORIZED_TEACHERS:
            print("Access granted: Teacher.")
            return "teacher"
        elif str(id) in AUTHORIZED_STUDENTS:
            print("Access granted: Student.")
            return "student"
        else:
            print("Access denied!")
            return "denied"
    finally:
        GPIO.cleanup()

# Function for facial recognition
def facial_recognition():
    print("Initializing facial recognition...")
    face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')
    cap = cv2.VideoCapture(0)

    while True:
        ret, frame = cap.read()
        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        faces = face_cascade.detectMultiScale(gray, 1.1, 4)

        for (x, y, w, h) in faces:
            cv2.rectangle(frame, (x, y), (x+w, y+h), (255, 0, 0), 2)
            print("Face detected!")
            cap.release()
            cv2.destroyAllWindows()
            return True

        cv2.imshow('Facial Recognition', frame)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break

    cap.release()
    cv2.destroyAllWindows()
    return False

# Main function
def main():
    print("Starting Trackify system...")

    while True:
        distance = check_ultrasonic()
        if distance < 50:  # If a person is detected nearby
            print(f"Person detected at {distance:.2f} cm. Waiting for RFID card...")
            user_role = rfid_authentication()

            if user_role == "denied":
                print("Access denied. System reset.")
                continue

            if facial_recognition():
                print(f"Attendance marked for {user_role}.")
            else:
                print("Facial recognition failed. Access denied.")

        time.sleep(1)

# Run the system
if __name__ == "__main__":
    main()



Key Features Integrated:
Ultrasonic Sensor:

Detects nearby individuals.
Triggers RFID and facial recognition systems.
RFID Reader:

Identifies users as teachers or students.
Grants or denies access based on preloaded UIDs.
Facial Recognition:

Confirms the identity of users detected via RFID.
Uses OpenCV for facial detection.
Attendance Management:

Logs attendance if both RFID and facial recognition succeed.




Trackify/
├── src/
│   ├── trackify_main.py       # Main integrated script
├── docs/
│   ├── architecture.png       # System architecture diagram
│   ├── chatbot-demo.png       # Chatbot screenshots
│   ├── dashboards/            # Dashboards images
├── database/
│   ├── attendance.db          # SQLite database for logging attendance
├── README.md                  # Project documentation



pip install opencv-python RPi.GPIO mfrc522

python trackify_main.py






