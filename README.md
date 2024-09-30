# Posture Corrector Application

## Overview
This project is a **real-time posture detection tool** that uses the **MediaPipe** library for pose estimation and **OpenCV** for video capture and display. It detects key body landmarks such as shoulders and ears, calculates angles, and provides feedback on the user's posture. The application will notify the user via a visual display and sound alert when poor posture is detected.


## Features
### Pose detection
- Detects key landmarks like shoulders and ears using MediaPipe's Pose solution.
- Continuously tracks and updates positions in real-time using a webcam.
### Angle Calculation
- Calculates the angles between key points (e.g., shoulder angle, neck angle) to assess posture.
### Calibration
- Initially calibrates based on the user’s natural posture for the first 30 frames.
- Thresholds are established for the shoulder and neck angles to compare with subsequent measurements.
### Feedback
- Displays the current posture status (e.g., "Good Posture" or "Poor Posture").
- Plays a sound alert if poor posture is detected.
- Displays angles and posture status directly on the video feed.

## Setup & Requirements
### Prerequisites
* Python 3.x
* OpenCV (cv2)
* MediaPipe (mediapipe)
* NumPy (numpy)
* playsound (playsound)
* A webcam for video input
  
### Install required packages:
```bash
pip install opencv-python mediapipe numpy playsound
```
### Optional
To play the sound alert, place a .mp3 or .wav file in the same directory as the script and set the sound_file variable.
  
### Running the Application
```bash
python posture_corrector.py
```
## How It Works

1. **Capture Video:** The webcam is opened, and frames are captured in real-time.

2. **Pose Detection**
   - The frame is processed through MediaPipe's pose detector to extract landmarks for the shoulders and ears.

3. **Angle Calculation:**
   - Angles between the shoulders and neck are calculated based on the detected landmarks.
   - A threshold is set for these angles during the calibration phase.

4. **Calibration:**
   - During the first 30 frames, the application collects data to calibrate the user’s natural posture.
   - After calibration, the shoulder and neck angle thresholds are calculated, and the system begins posture analysis.

5. **Posture Feedback:**
   - If the user's posture deviates from the calibrated posture, a "Poor Posture" warning is displayed, and an alert sound is played.
   - Otherwise, "Good Posture" is shown with the current shoulder and neck angles.

6. **Exit:**
   - Press 'q' to quit the application.

## Customization
- **Calibration Frames:** Adjust the number of frames for calibration by changing the calibration_frames variable.
- **Alert Cooldown:** Modify alert_cooldown to set how often the sound alert should play after detecting poor posture.
