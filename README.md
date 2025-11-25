# Advanced-Safety-Monitoring-System
A comprehensive computer vision and IoT-based safety monitoring system that combines face recognition, Personal Protective Equipment (PPE) detection, and real-time sensor monitoring with automated WhatsApp alerts.

##🚀 Features
##🔍 Face Recognition & Monitoring

    1. Real-time face detection and recognition using OpenCV's YuNet and SFace models

    2. Support for multiple registration methods (images or camera capture)

    3. Configurable distance metrics (Cosine Similarity or Norm-L2 Distance)

    4. Live video feed from webcam or video files

##🛡️ PPE Violation Detection
    1. YOLO-based detection of safety equipment violations:

        Hardhat

        Mask

        Safety Vest

        Gloves

        Goggles

        Safety Shoes

    2. Real-time violation alerts with bounding boxes and confidence scores

##📊 IoT Sensor Integration

   1. Real-time sensor data monitoring via UDP:

        Heart Rate (BPM)

        Temperature (°C)

        Humidity (%)

        Atmospheric Pressure (hPa)

   2. Configurable safety thresholds for health risk detection

##📱 Automated WhatsApp Alerts

    1. Instant PPE violation alerts with annotated images

    2. Health risk notifications for abnormal sensor readings

    3. Rate-limited alerts (maximum one per minute per category)

    4. Professional alert templates with safety protocols

##🛠️ Installation
Prerequisites

    1. Python 3.8+

    2. Webcam or video source

    3. WhatsApp account for alert system

##Required Libraries
bash

pip install -r requirements.txt

Required Models & Files

    Face detection model: face_detection_yunet_2023mar.onnx

    Face recognition model: face_recognition_sface_2021dec_int8.onnx

    YOLO PPE detection model: Custom trained model (update path in code)

## 📋 Usage
1. System Setup
python

# Configure WhatsApp recipient
WHATSAPP_CONFIG = {
    'phone_number': '+966549256227',  # Replace with actual number
}

# Adjust sensor thresholds as needed
SENSOR_THRESHOLDS = {
    'pulse_high': 130,
    'pulse_low': 45,
    'temp_high': 40,
    # ... other thresholds
}

2. Face Registration

    Method 1: Select multiple images and register with name

    Method 2: Quick registration using live camera feed

    Manage registered faces (save/load/delete)

3. Safety Monitoring

    Choose video source (webcam or file)

    Enable/disable PPE detection

    Start monitoring with real-time display

    View recognition results and violation alerts

4. Sensor Integration

    System automatically listens for UDP sensor data on port 5005

    Sensor data displayed in real-time with health status

    Automatic WhatsApp alerts for critical readings

##🏗️ System Architecture
Components

    FaceRecognitionApp: Main GUI application

    FaceRecognitionThread: Real-time video processing

    FaceRegistrationThread: Background face registration

    SensorReceiverThread: UDP sensor data reception

    WhatsAppAlertSystem: Alert management and delivery

Alert Flow

    PPE Violation: Detection → Annotated Image → WhatsApp Alert

    Sensor Alert: Threshold Breach → Health Risk Assessment → WhatsApp Alert

    Rate Limiting: Maximum one alert per minute per category

##⚙️ Configuration
Sensor Data Format
json

{
  "bpm": 75,
  "temp_c": 36.5,
  "rh": 45.0,
  "press_hpa": 1013.25
}

Alert Thresholds

    Pulse: High > 130 BPM, Low < 45 BPM

    Temperature: Critical > 40°C

    Humidity: Critical > 75% with high temperature

    Pressure: Critical < 940 hPa

##🎯 Key Features
Smart Alert Management

    Prevents alert spam with minute-based rate limiting

    Enhanced annotated images for PPE violations

    Professional message templates with safety protocols

Multi-threaded Architecture

    Non-blocking GUI during processing

    Concurrent sensor and video processing

    Background WhatsApp message delivery

Data Persistence

    Save/load registered face embeddings

    Configurable model paths

    Flexible video source selection

##🚨 Alert Examples
PPE Violation Alert
text

##🚨 PPE VIOLATION DETECTED 🚨

Time: 2024-01-15 14:30:25

Violation Details:
- NO-Hardhat (Confidence: 0.87)
- NO-Safety Vest (Confidence: 0.92)

Location: Construction Site
Action Required: Immediate supervisor notification

Health Risk Alert
text

##⚠️ HEALTH RISK ALERT ⚠️

Time: 2024-01-15 14:35:10

Current Readings:
❤️ BPM: 145
🌡️ Temp: 41.2°C
💧 Humidity: 80%

Detected Violations:
⚠️ Very high pulse (145 BPM) - dangerous for worker
⚠️ Extremely high temperature (41.2°C) - heat stress risk

##🔧 Troubleshooting
Common Issues

    Webcam not detected: Check camera permissions and try video file

    Models not loading: Verify model file paths and permissions

    WhatsApp sending failed: Ensure stable internet connection and valid phone number

    Sensor data not received: Check UDP port and data format

##Performance Tips

    Use GPU acceleration for YOLO model if available

    Reduce video resolution for better performance

    Close other applications during monitoring

📄 License

This project is for educational and research purposes. Ensure compliance with local regulations regarding surveillance and data privacy.
##🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.
##⚠️ Disclaimer

This system is designed for safety monitoring in controlled environments. Always ensure proper consent and compliance with privacy laws when deploying facial recognition systems.

