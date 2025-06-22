import RPi.GPIO as GPIO
import time

# GPIO pin where the servo signal wire is connected
servo_pin = 18  # BCM pin 18 = physical pin 12

GPIO.setmode(GPIO.BCM)
GPIO.setup(servo_pin, GPIO.OUT)

# Initialize PWM at 50Hz
pwm = GPIO.PWM(servo_pin, 50)
pwm.start(0)

# Function to rotate servo to a specific angle (0 to 180 degrees)
def set_angle(angle):
    duty = 2.5 + (angle / 180.0) * 10  # Map angle to duty cycle
    pwm.ChangeDutyCycle(duty)
    print(f"Moving to {angle}° (Duty Cycle: {duty:.2f}%)")
    time.sleep(0.5)

def run_servo_sequence():
    set_angle(0)
    time.sleep(1)
    set_angle(90)
    time.sleep(1)
    set_angle(0)
    time.sleep(1)
    set_angle(180)
    time.sleep(1)
    set_angle(0)
    time.sleep(1)

try:
    print("Type 'start' to begin, or 'x' to exit.")
    while True:
        command = input("Command: ").strip().lower()

        if command == 'start':
            print("Running servo sequence...")
            run_servo_sequence()
            print("Sequence completed. Awaiting next command...")

        elif command == 'x':
            print("Exiting program.")
            break

        else:
            print("Unknown command. Use 'start' or 'x'.")

except KeyboardInterrupt:
    print("\nStopped by user (Ctrl+C).")

finally:
    pwm.stop()
    GPIO.cleanup()
