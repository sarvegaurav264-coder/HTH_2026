# HTH_2026
Smart Health Monitoring & Gesture-Enabled Glove

A wearable smart-glove prototype designed for continuous patient health monitoring, gesture detection, emergency alerting, and remote caregiver visibility.

1. Project Overview

The Smart Health Monitoring Glove is a wearable healthcare prototype that combines vital-sign monitoring and hand-gesture detection in a single glove.

The system is designed especially for patients who may need continuous observation, including elderly or physically challenged users. Instead of depending completely on manual checking or multiple separate devices, the glove collects health data through embedded sensors and sends the information through an ESP32-based wireless system.

The goal is to make monitoring:

Continuous

Simple to use

Comfortable for the patient

Easier for caregivers

Less dependent on manual supervision

Capable of generating timely alerts

2. Problem Statement

Existing patient-monitoring approaches have several practical limitations:

Many devices monitor only a limited number of health parameters.

Manual monitoring can be inconsistent and error-prone.

Continuous supervision by caregivers is not always feasible.

Some monitoring devices are difficult for elderly patients to operate.

Existing wearable systems can be costly or uncomfortable.

Different devices may not communicate effectively with each other.

Emergency alerting and location tracking are not always integrated into the monitoring workflow.

Core Challenge

The challenge is to develop a simple, wearable and connected monitoring system that can continuously collect patient data, detect relevant hand gestures, and help caregivers respond quickly when attention is required.

3. Proposed Solution

We propose a Smart Health Monitoring Glove with embedded sensing and wireless connectivity.

The glove combines:

Vital-sign sensing
A pulse sensor is integrated into the glove to capture pulse/heart-rate information.

Hand-gesture detection
Hand/finger movements can be detected and interpreted as predefined gestures.

ESP32 processing and connectivity
The ESP32 acts as the main controller and provides Wi-Fi connectivity for transmitting data.

Remote monitoring
Sensor readings and relevant events can be sent to a software/cloud layer for caregiver monitoring.

Emergency alert workflow
When a predefined emergency condition or gesture is detected, the system can trigger an alert.

Location support
Location information can be integrated into the emergency-alert workflow through a suitable GPS/phone/location source.

4. Key Features

Health Monitoring

Continuous pulse/heart-rate monitoring

Sensor data acquisition through the wearable glove

Real-time data processing by ESP32

Monitoring data can be transmitted wirelessly

Gesture Recognition

Detect predefined hand gestures

Use gestures as simple commands or emergency signals

Reduce the need for complicated buttons or interfaces

Emergency Alerts

Detect predefined emergency conditions/gestures

Trigger an alert to the caregiver/monitoring system

Support location information with the alert when a location source is available

Patient-Friendly Design

Wearable form factor

Simple interaction

Designed with elderly and physically challenged users in mind

Reduces dependency on complex monitoring equipment

Connectivity

ESP32-based Wi-Fi communication

Remote data transmission

Can be connected to a dashboard/cloud backend

5. How the System Works

Basic Flow

                PATIENT WEARS GLOVE
                        |
                        v
              +-------------------+
              | Embedded Sensors  |
              |                   |
              | Pulse Sensor      |
              | Gesture Sensing   |
              +---------+---------+
                        |
                        v
                 +-------------+
                 |    ESP32    |
                 | Processing  |
                 +------+------+ 
                        |
             +----------+----------+
             |                     |
             v                     v
      Health Data             Gesture/Event
      Processing              Recognition
             |                     |
             +----------+----------+
                        |
                        v
                 Wi-Fi Connectivity
                        |
                        v
              +---------------------+
              | Monitoring / Cloud  |
              |      Layer          |
              +----------+----------+
                         |
             +-----------+-----------+
             |                       |
             v                       v
       Caregiver View          Emergency Alert
                                     |
                                     v
                              Location Data*

* Location requires an available GPS, smartphone, or other location source integrated with the prototype.

6. System Architecture

The project can be divided into four major layers.

Layer 1 — Wearable Sensing Layer

Responsible for collecting information from the patient.

Components:

Pulse sensor

Gesture sensing mechanism

Wearable glove

Layer 2 — Edge Processing Layer

The ESP32 receives sensor readings and processes the data locally.

Responsibilities:

Read sensor values

Process/validate readings

Detect predefined events

Handle gesture input

Manage Wi-Fi communication

Layer 3 — Communication Layer

The ESP32 uses Wi-Fi to transmit relevant information to the monitoring system.

Possible data:

Pulse/heart-rate readings

Gesture/event status

Alert status

Device status

Timestamp

Location information when available

Layer 4 — Monitoring & Alert Layer

The received data can be displayed through a dashboard or monitoring interface.

The system can provide:

Patient status

Live/periodic readings

Detected gestures

Emergency notifications

Device connectivity status

Location during supported emergency events

7. Hardware Components

Component

Purpose

Wearable Glove

Physical platform for the system

ESP32

Main microcontroller + Wi-Fi connectivity

Pulse Sensor Module

Measures pulse/heart-rate signal

Gesture Sensing Module

Detects predefined hand/finger movements

Connecting Wires

Electrical connections

Power Source

Powers the wearable prototype

Location Source*

Provides location during emergency workflow

*Use only if included in the actual prototype. Location can alternatively be obtained through a connected phone/application.

8. Software Components

The software side can contain:

ESP32 firmware

Sensor data processing

Gesture/event detection logic

Wi-Fi communication

Backend/cloud API

Monitoring dashboard

Alert/notification service

Suggested Technology Stack

Embedded

ESP32

Arduino IDE / PlatformIO

C/C++

Backend

Node.js

Express.js

Database / Cloud

Firebase / MongoDB / other suitable backend

Frontend

HTML/CSS/JavaScript or React

The final stack can be changed according to the implementation used by the team.

9. Data Flow

Pulse Sensor
     |
     v
  ESP32  <----- Gesture Sensor
     |
     | Process & Validate
     v
 Wi-Fi Communication
     |
     v
 Backend / Cloud
     |
     +----------------------+
     |                      |
     v                      v
Dashboard              Alert Service
     |                      |
     v                      v
Caregiver             Emergency Contact
                            |
                            v
                       Location Data*

10. Example Data Structure

A monitoring record can follow a structure similar to:

{
  "deviceId": "GLOVE_001",
  "timestamp": "2026-09-28T10:30:00Z",
  "heartRate": 78,
  "gesture": "NORMAL",
  "alert": false,
  "location": {
    "latitude": null,
    "longitude": null
  }
}

The actual fields and thresholds should be finalized according to the hardware and software implementation.

11. Emergency Workflow

A simplified emergency workflow is:

Sensor / Gesture Input
        |
        v
   ESP32 Processing
        |
        v
 Is Emergency Condition
       Detected?
      /          \
    NO            YES
    |              |
    v              v
Continue       Create Alert
Monitoring         |
                   v
             Attach Location*
                   |
                   v
             Send Notification
                   |
                   v
              Caregiver

The prototype should use clearly defined event rules so that accidental movements do not unnecessarily trigger emergency notifications.

12. Gesture-Based Interaction

The glove can support predefined gestures.

Example concept:

Gesture/Event

Possible Function

Normal hand position

Normal monitoring

Predefined help gesture

Request assistance

Emergency gesture

Trigger emergency alert

Other configured gesture

Application-specific command

The exact gestures should be finalized after testing the selected gesture-sensing hardware.

13. Why This Solution Is Different

The project focuses on combining multiple useful functions into one wearable platform:

Vital monitoring + gesture interaction

Wearable and patient-friendly form factor

ESP32-based wireless connectivity

Reduced dependence on continuous manual checking

Potential offline/edge processing for immediate local decisions

Simple caregiver monitoring workflow

Emergency alert capability

Expandable architecture for additional sensors

Important Differentiator

The objective is not simply to create another pulse-monitoring device.

The key idea is to create a single wearable interaction and monitoring layer where:

Patient → Sensors → ESP32 → Data/Event Processing → Caregiver/Alert System

14. Advantages

For Patients

Simple wearable interaction

Less need to operate complex devices

Continuous monitoring support

Gesture-based assistance mechanism

For Caregivers

Remote visibility of patient status

Faster awareness of predefined emergency events

Reduced need for constant manual checking

Centralized monitoring interface

For Healthcare Environments

Low-complexity prototype architecture

Expandable sensor design

Wireless communication

Potential integration with future healthcare systems

15. Reliability & Safety Considerations

This prototype is intended as a hackathon proof-of-concept, not as a certified medical device.

Important considerations for future development:

Sensor readings must be validated against clinically accepted devices.

False positives and false negatives should be tested.

Emergency thresholds must be determined through appropriate medical guidance.

The device should not be treated as a replacement for professional medical monitoring.

Patient data should be transmitted securely.

Authentication and access control should be implemented before real-world deployment.

Battery and thermal safety should be tested for continuous wearable use.

The glove should be designed to avoid discomfort during long-duration use.

16. Repository Structure

A suggested GitHub repository structure:

smart-health-monitoring-glove/
│
├── README.md
│
├── firmware/
│   ├── esp32/
│   │   ├── main.ino
│   │   ├── sensors/
│   │   ├── gesture/
│   │   └── communication/
│   │
│   └── README.md
│
├── hardware/
│   ├── circuit/
│   ├── wiring/
│   ├── schematics/
│   └── BOM.md
│
├── backend/
│   ├── server.js
│   ├── routes/
│   ├── controllers/
│   └── README.md
│
├── dashboard/
│   ├── src/
│   └── README.md
│
├── docs/
│   ├── architecture.md
│   ├── system-flow.md
│   └── testing.md
│
├── images/
│   ├── prototype.jpg
│   ├── architecture.png
│   └── circuit.png
│
└── LICENSE

17. Getting Started

Step 1 — Clone the Repository

git clone https://github.com/<your-username>/smart-health-monitoring-glove.git
cd smart-health-monitoring-glove

Step 2 — Hardware Setup

Connect the pulse sensor and gesture-sensing hardware to the ESP32 according to the final circuit diagram.

Step 3 — Configure ESP32

Install the required ESP32 board package and required libraries in Arduino IDE or PlatformIO.

Update:

Wi-Fi SSID

Wi-Fi password

Backend/API endpoint

Sensor pins

Gesture configuration

Step 4 — Upload Firmware

Upload the ESP32 firmware to the board.

Step 5 — Start Backend

If a Node.js backend is used:

cd backend
npm install
npm start

Step 6 — Run Dashboard

If a frontend/dashboard is included:

cd dashboard
npm install
npm run dev

18. Configuration

Do not commit sensitive credentials to GitHub.

Use environment variables for:

WIFI_SSID
WIFI_PASSWORD
API_URL
DATABASE_URL
API_KEY

Add sensitive files such as .env to .gitignore.

Example:

.env
node_modules/
build/
dist/
*.log

19. Testing Plan

Hardware Testing

Verify ESP32 power supply

Verify pulse sensor readings

Verify gesture sensor readings

Verify sensor wiring

Verify Wi-Fi connectivity

Verify data transmission

Software Testing

Sensor data validation

Gesture detection testing

Emergency event testing

API communication testing

Dashboard data display

Alert delivery testing

User Testing

Glove comfort

Ease of wearing

Gesture usability

Readability of monitoring interface

Response time of alerts

20. Future Scope

The architecture can be extended with additional capabilities:

SpO₂ monitoring

Body temperature monitoring

Additional motion sensors

Fall detection

ECG integration

GPS integration

Mobile application

SMS/app notifications

Advanced caregiver dashboard

Historical health-data visualization

Secure patient profiles

Multi-patient monitoring

AI-assisted anomaly detection

Battery optimization

Offline data buffering and synchronization

21. Project Roadmap

Phase 1 — Prototype

Integrate ESP32

Integrate pulse sensor

Integrate gesture sensing

Build wearable glove

Establish Wi-Fi communication

Phase 2 — Monitoring

Create backend

Store sensor readings

Build caregiver dashboard

Add event/alert handling

Phase 3 — Reliability

Test sensor accuracy

Reduce false alerts

Improve power efficiency

Improve wearable comfort

Add secure communication

Phase 4 — Advanced Healthcare Integration

Add additional vital sensors

Add location integration

Add mobile application

Add historical analytics

Validate with appropriate healthcare professionals

22. Current Prototype Scope

Implemented / Prototype Focus

Wearable glove concept

ESP32-based processing

Pulse sensing

Gesture detection concept

Wireless connectivity concept

Caregiver monitoring concept

Emergency alert workflow

Planned / Extendable

Full cloud backend

Production-ready dashboard

Dedicated GPS integration

Additional vital-sign sensors

Secure authentication

Clinical validation

Long-duration battery optimization

23. Impact

The project aims to make patient monitoring more accessible, connected, and easier to operate.

Instead of relying only on manual observation:

Manual Monitoring
       ↓
Limited Observation
       ↓
Possible Delay

the proposed workflow is:

Wearable Monitoring
       ↓
Continuous Data Collection
       ↓
Event Detection
       ↓
Wireless Communication
       ↓
Caregiver Awareness
       ↓
Faster Response

24. Hackathon Pitch in One Line

“Our Smart Health Monitoring Glove combines vital-sign sensing and gesture-based interaction in one wearable device, using ESP32 connectivity to support continuous monitoring and timely caregiver alerts.”

25. Team

Project: Smart Health Monitoring & Gesture-Enabled Glove

Hackathon: Hardware Hackathon

Team Members:

Add team member names here

26. Disclaimer

This project is a hackathon prototype intended for demonstration and research purposes. It is not a certified medical device and should not be used for diagnosis, treatment, or emergency medical decision-making without appropriate validation and professional oversight.

27. License

Add the project's selected open-source license here, for example:

MIT License

28. Acknowledgement

Built as a hardware-focused hackathon prototype to explore wearable health monitoring, gesture-based interaction, embedded systems, and connected healthcare technology.
