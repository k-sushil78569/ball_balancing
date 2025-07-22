# Ball Balancing Plate Using PiCamera and Servos

This project is a real-time ball balancing system using Raspberry Pi, PiCamera2, OpenCV, and three servo-controlled arms. The system detects an orange ball on a plate and adjusts the tilt to bring the ball back to the center using PID control.

## 📷 Features

- Live video capture and HSV-based ball detection
- Cartesian coordinate mapping from image frame
- PID controller to calculate required tilt angle
- Inverse kinematics to control servo angles
- Real-time visualization of tracking and mask

## ⚙️ Hardware Requirements

- Raspberry Pi 4/3 with PiCamera2 module
- 3x Servo motors (SG90 or similar)
- GPIO pins for PWM control
- Ball and plate setup for balancing

## 🧪 Software Requirements

- Python 3.7+
- OpenCV (`cv2`)
- NumPy
- PiCamera2 (`picamera2`)
- RPi.GPIO

## 🧠 PID & IK Explanation

- **PID Control**: Compares the ball position to the center and calculates corrective movement.
- **Angle Calculation**: Converts movement direction (theta) and magnitude (phi) into servo angles using inverse kinematics.

## 🎯 How It Works

1. Captures video feed from PiCamera.
2. Applies Gaussian blur and HSV masking to detect an orange ball.
3. Computes ball position relative to center.
4. Runs PID control to compute required tilt direction and angle.
5. Uses inverse kinematics to calculate each servo arm's required angle.
6. Sends angle as PWM signal to corresponding servo.

## 🖱️ Debugging Tools

- Hover your mouse over the "HSV" window to print HSV values of any pixel.
- Use this to fine-tune the `lower_orange` and `upper_orange` HSV ranges.

## 🛑 Stopping

To stop the program safely, press `q` while the "Ball Tracking" window is focused.

## 🧹 Cleanup

The program handles GPIO and window cleanup automatically upon exit.

## 📎 Notes

- Servo angles are constrained between 80°–150° to prevent damage.
- PID constants and camera alignment (`theta + 45`) may require tuning.
