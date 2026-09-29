# 🦾 Smart Assistive Hand Gloves for Visually Impaired

> **An AI-powered assistive glove that uses Computer Vision, IoT sensors, and real-time audio feedback to help visually impaired individuals detect obstacles and recognize surrounding objects.**

<p align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge\&logo=python)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Computer%20Vision-green?style=for-the-badge)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-red?style=for-the-badge\&logo=opencv)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep%20Learning-orange?style=for-the-badge\&logo=tensorflow)
![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-IoT-red?style=for-the-badge\&logo=raspberrypi)
![Firebase](https://img.shields.io/badge/Firebase-Cloud-yellow?style=for-the-badge\&logo=firebase)
![Twilio](https://img.shields.io/badge/Twilio-Emergency%20Communication-red?style=for-the-badge\&logo=twilio)

</p>

---

## 📌 Overview

The **Smart Assistive Hand Gloves** project is an AI and IoT-based wearable system designed to provide real-time environmental assistance to visually impaired users.

The system combines:

* 👁️ **Computer Vision** for object recognition
* 🤖 **YOLOv8** for real-time object detection
* 📡 **Ultrasonic sensing** for obstacle detection
* 🔊 **Voice feedback** through Bluetooth headphones
* ☁️ **Firebase** for cloud synchronization
* 🚨 **Twilio API** for emergency communication
* 🥧 **Raspberry Pi** as the edge computing platform

The objective is to transform visual information from the user's surroundings into **audio-based guidance**, allowing users to better understand nearby objects and obstacles.

---

## 🎯 Key Features

### 👁️ Real-Time Object Detection

Uses **YOLOv8** to identify objects from a camera feed in real time.

Detected objects can be converted into audio notifications such as:

> "Person detected"

> "Chair detected"

> "Car detected"

---

### 📡 Obstacle Detection

An ultrasonic sensor continuously measures the distance between the user and nearby obstacles.

If an obstacle enters a predefined safety range, the system triggers an alert.

```text
Ultrasonic Sensor
       ↓
Distance Measurement
       ↓
Safety Threshold
       ↓
Obstacle Detected
       ↓
Audio Alert
```

---

### 🔊 Audio Assistance

Visual detection results are converted into voice notifications and delivered through **Bluetooth headphones**.

This allows the user to receive environmental information without needing a visual display.

---

### 🚨 Emergency Communication

The system integrates the **Twilio API** to support emergency communication.

In an emergency scenario, the system can trigger an alert/message to a predefined contact.

---

### ☁️ Firebase Cloud Synchronization

Firebase is used for cloud-based data synchronization and communication between the assistive system and backend services.

---

### 🧹 Dataset & Label Processing

The computer vision pipeline includes dataset preparation and cleanup, including:

* COCO-format labels
* Image-label validation
* Unmatched image cleanup
* Dataset organization
* Object detection preprocessing

---

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │       Camera        │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │     OpenCV           │
                    │ Image Processing     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      YOLOv8         │
                    │ Object Detection    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Detection Results   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Voice Feedback    │
                    │ Bluetooth Headset   │
                    └─────────────────────┘


      ┌─────────────────────┐
      │ Ultrasonic Sensor   │
      └──────────┬──────────┘
                 │
                 ▼
      ┌─────────────────────┐
      │ Distance Calculation│
      └──────────┬──────────┘
                 │
                 ▼
      ┌─────────────────────┐
      │ Obstacle Detection  │
      └──────────┬──────────┘
                 │
                 ▼
      ┌─────────────────────┐
      │   Audio Warning     │
      └─────────────────────┘


      ┌─────────────────────┐
      │   Raspberry Pi       │
      │ Edge Processing      │
      └──────────┬──────────┘
                 │
          ┌──────┴──────┐
          ▼             ▼
     ┌─────────┐   ┌─────────┐
     │Firebase │   │ Twilio  │
     │  Cloud  │   │Emergency│
     └─────────┘   └─────────┘
```

---

## 🔄 How It Works

```text
Camera captures surroundings
            ↓
      OpenCV processing
            ↓
       YOLOv8 inference
            ↓
     Object identification
            ↓
     Convert result to speech
            ↓
    Bluetooth audio feedback
```

At the same time:

```text
Ultrasonic sensor
        ↓
Measure distance
        ↓
Compare with threshold
        ↓
Obstacle detected?
      ↙       ↘
    YES        NO
     ↓          ↓
Audio Alert   Continue
```

---

## 🛠️ Technology Stack

| Category         | Technology              |
| ---------------- | ----------------------- |
| Programming      | Python                  |
| Computer Vision  | OpenCV                  |
| Object Detection | YOLOv8                  |
| Deep Learning    | TensorFlow              |
| Edge Computing   | Raspberry Pi            |
| Distance Sensing | Ultrasonic Sensor       |
| Audio            | Bluetooth Headphones    |
| Cloud            | Firebase                |
| Communication    | Twilio API              |
| Dataset          | COCO-format annotations |

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Smart-Assistive-Hand-Gloves.git

cd Smart-Assistive-Hand-Gloves
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it:

**Windows**

```bash
venv\Scripts\activate
```

**Linux / Raspberry Pi**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

Run the main application:

```bash
python main.py
```

The system initializes:

1. Camera
2. YOLOv8 model
3. Ultrasonic sensor
4. Audio feedback
5. Firebase connection
6. Emergency communication module

---

## 🧠 Object Detection

The project uses YOLOv8 for real-time object recognition.

Example inference flow:

```python
from ultralytics import YOLO

model = YOLO("models/best.pt")

results = model(source=0, show=True)
```

The detected objects are then processed and converted into meaningful audio feedback.

---

## 📊 Performance

The system achieved approximately:

### **90% Accuracy in Dynamic Conditions**

Performance was evaluated under changing environmental conditions to test the robustness of the assistive system.

> **Important:** If you have exact metrics such as precision, recall, mAP@50, FPS, or inference latency, replace the single accuracy figure with those measurements. They make the project substantially more reproducible and credible.

---

## 🔐 Emergency Alert System

The emergency communication module uses Twilio to send an alert to a predefined emergency contact.

```text
Emergency Event
      ↓
System Detection
      ↓
Twilio API
      ↓
Emergency Message
      ↓
Registered Contact
```

**Security note:** Never commit API keys, authentication tokens, Firebase credentials, or other secrets to GitHub.

Use environment variables instead:

```env
TWILIO_ACCOUNT_SID=your_account_sid
TWILIO_AUTH_TOKEN=your_auth_token
TWILIO_PHONE_NUMBER=your_twilio_number
EMERGENCY_PHONE_NUMBER=your_contact_number
```

---

## ☁️ Firebase Integration

Firebase provides cloud synchronization for system-related data.

```text
Smart Glove
     ↓
Raspberry Pi
     ↓
Firebase
     ↓
Cloud Data
```

This architecture allows the system to synchronize relevant information while keeping the core computer-vision processing at the edge.

---

## 🚀 Future Improvements

Potential improvements include:

* [ ] Improve object detection accuracy
* [ ] Add more object classes
* [ ] Optimize YOLOv8 for Raspberry Pi
* [ ] Implement TensorRT / ONNX optimization
* [ ] Reduce inference latency
* [ ] Add GPS-based location tracking
* [ ] Add fall detection
* [ ] Add voice commands
* [ ] Improve multilingual voice assistance
* [ ] Add battery monitoring
* [ ] Build a mobile companion application
* [ ] Add obstacle direction estimation
* [ ] Deploy a lightweight edge AI model

---

## 🎥 Demo

> Add your project demonstration video here.

```text
📹 Demo Video:
[Coming Soon]
```

You can also add a GIF directly to your repository:

```markdown
![Project Demo](assets/demo.gif)
```

---

## 📸 Project Gallery

Add photographs of:

* Smart glove hardware
* Raspberry Pi setup
* Camera module
* Ultrasonic sensor
* Object detection output
* User testing
* Final prototype

```markdown
![Smart Glove](assets/smart-glove.jpg)
![Object Detection](assets/object-detection.jpg)
![Hardware Setup](assets/hardware.jpg)
```

---

## 🌟 Why This Project?

This project demonstrates the combination of several real-world engineering areas:

```text
Artificial Intelligence
        +
Computer Vision
        +
IoT
        +
Edge Computing
        +
Cloud
        +
Real-Time Systems
        ↓
Assistive Technology
```

Rather than building a standalone machine-learning model, the project integrates **AI inference, physical sensors, edge computing, cloud services, and real-time user interaction** into a single assistive system.

---

## 👨‍💻 Skills Demonstrated

* Python Development
* Computer Vision
* Deep Learning
* YOLOv8
* Object Detection
* OpenCV
* TensorFlow
* Raspberry Pi
* IoT Integration
* Sensor Programming
* Firebase
* REST/API Integration
* Twilio API
* Dataset Preparation
* Real-Time AI Systems
* Edge AI

---

## 📜 License

This project is intended for educational and research purposes.

If you plan to open-source the project, add an appropriate license such as MIT:

```text
MIT License
```

---

## ⭐ Support

If you found this project interesting, consider giving the repository a ⭐.

Your feedback and suggestions are welcome!

---

### 👤 Author

**Siddharth Gunjal**

AI Engineer | Computer Vision | Generative AI | Machine Learning

---

<p align="center">

**Built with Python • YOLOv8 • OpenCV • Raspberry Pi • Firebase**

</p>
