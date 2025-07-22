## 📂 File Descriptions (Main Code Folder)

- **`angle_servo.py`**  
  ➤ Calculates the servo angles required to tilt the platform, based on the PID output.  
  ➤ Converts tilt direction (`theta`) and magnitude (`phi`) into servo commands using inverse kinematics.

- **`pid.py`**  
  ➤ Takes the ball's position from the camera and computes the PID output.  
  ➤ Determines how much and in which direction the platform should tilt to bring the ball back to center.

- **`camera_axis.py`**  
  ➤ Helps align the camera such that one of the servo arms (Arm 1) lies along the X-axis in the camera view.  
  ➤ This script tells you how much to **virtually rotate** the camera view.  
  ➤ The camera is **not physically rotated**—only the output angle is adjusted accordingly in the code.  
  ➤ Also helps align the coordinate center to the actual center of the plate.

- **`code_camera.py`**  
  ➤ Handles real-time video capture and HSV-based ball detection using the PiCamera.

- **`main.py`**  
  ➤ Fully integrated code that combines camera input, PID control, angle computation, and servo output.  
  ➤ This is the final script used to run the real-time ball-balancing system.

