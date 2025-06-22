import RPi.GPIO as GPIO
import time

# --- GPIO Setup ---
GPIO.setmode(GPIO.BCM)
servo_pins = [18, 23, 24]  # arm1, arm2, arm3

equilibrium_angles = [100, 100, 105]
tilt = 10  # degrees

direction_offsets = {
    "North":         [ 0, -tilt,  tilt],
    "North-East":    [-tilt, -tilt, tilt],
    "East":          [-tilt,  0, tilt],
    "South-East":    [-tilt, tilt,  tilt],
    "South":         [ 0,  tilt, -tilt],
    "South-West":    [ tilt, tilt, -tilt],
    "West":          [ tilt,  0, -tilt],
    "North-West":    [ tilt, -tilt, -tilt],
}

# --- Initialize PWM ---
pwms = []
for pin in servo_pins:
    GPIO.setup(pin, GPIO.OUT)
    pwm = GPIO.PWM(pin, 50)  # 50Hz PWM
    pwm.start(0)
    pwms.append(pwm)

# --- Set all 3 servo angles in parallel ---
def move_platform(target_angles):
    # Calculate duty cycles first
    duties = [2.5 + (angle / 180.0) * 10 for angle in target_angles]

    # Set all servos simultaneously
    for i in range(3):
        pwms[i].ChangeDutyCycle(duties[i])

    time.sleep(0.15)  # faster movement (3× speed)
    # Keep duty to maintain torque (no ChangeDutyCycle(0))

# --- Test 8 Directions ---
def try_platform_slope():
    print("Moving to equilibrium...")
    move_platform(equilibrium_angles)
    time.sleep(1)

    for direction, offsets in direction_offsets.items():
        target_angles = [
            equilibrium_angles[i] + offsets[i] for i in range(3)
        ]
        print(f"Tilt → {direction}: {target_angles}")
        move_platform(target_angles)
        time.sleep(5)
        print("Returning to equilibrium...")
        move_platform(equilibrium_angles)
        time.sleep(1)

# --- Main ---
try:
    print("Starting platform tilt test...")
    try_platform_slope()
    print("Test completed.")

except KeyboardInterrupt:
    print("Interrupted by user.")

finally:
    print("Cleaning up...")
    for pwm in pwms:
        pwm.stop()
    GPIO.cleanup()
