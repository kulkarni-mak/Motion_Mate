# Motion Mate: Pose Estimation on Raspberry Pi 4

Motion Mate is a real-time computer vision application designed for the Raspberry Pi 4. It performs human pose estimation by capturing video from a remote IP camera, processing anatomical landmarks through digital signal processing, and streaming the resulting motion data to a web-based dashboard.

---

## Project Overview

This project demonstrates the capability of edge computing devices to handle complex computer vision tasks. By utilizing a Raspberry Pi 4 as the host controller, the system isolates human movement from the environment, rendering a skeletal visualization on a high-contrast black canvas to ensure privacy and focus on motion dynamics.

### Core Features

* **Edge Processing:** Executes Google’s MediaPipe Pose model on the Raspberry Pi 4 to track 33 body landmarks in real-time.
* **Remote Vision Integration:** Connects to mobile device cameras via DroidCam, enabling wireless video acquisition without tethering hardware to the Pi.
* **Privacy-Centric Visualization:** Subtracts the original video background, displaying only the processed skeletal data.
* **Network-Based Streaming:** Implements a Flask web server to distribute the processed feed to any device on the local network.

---

## Technical Architecture
 **Compute Hardware** :Raspberry Pi 4 (Model B) 
 **Camera Source** : Mobile Device (via DroidCam) 
 **Detection Library** : MediaPipe (Pose Solution) 
 **Backend Framework** : Flask (Python) 
 **Vision Library** : OpenCV 
 **Matrix Operations** : NumPy 

---

## Raspberry Pi 4 Optimization

To maintain a stable frame rate on the Pi's ARM architecture, the system is configured as follows:

* **Model Complexity:** Set to `1` to balance accuracy with the Pi 4’s CPU performance.
* **Memory Management:** Utilizes NumPy for efficient frame manipulation, minimizing latency during the background subtraction process.
* **Network Hosting:** The Flask server is configured to host on `0.0.0.0`, allowing the Pi to act as a standalone IoT hub accessible via its local IP address.

---

## Setup and Installation

### 1. System Preparation

Update the Raspberry Pi OS and install necessary system dependencies:

```bash
sudo apt update && sudo apt upgrade

```

### 2. Environment and Dependencies

It is recommended to install the necessary libraries within a Python environment:

```bash
pip install opencv-python mediapipe flask numpy

```

### 3. Configuration

Update the `DROIDCAM_URL` in the script with the IP address of your mobile device:

```python
DROIDCAM_URL = "http://10.200.195.57:4747/video"

```

### 4. Running the System

Execute the script from the Raspberry Pi terminal:

```bash
python motion_mate.py

```

### 5. Remote Viewing

Access the live stream from any browser on your network by navigating to:
`http://<your-pi-ip-address>:5000`

---

