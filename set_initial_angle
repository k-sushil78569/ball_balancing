import RPi.GPIO as GPIO
import time

# Define GPIO pins for the three servos
servo_pins = [18, 23, 24]  # BCM pin numbers

GPIO.setmode(GPIO.BCM)

# Setup all pins as output and initialize PWM
pwms = []
for pin in servo_pins:
    GPIO.setup(pin, GPIO.OUT)
    pwm = GPIO.PWM(pin, 50)  # 50Hz PWM frequency
    pwm.start(0)
    pwms.append(pwm)

def set_servo_angle(pwm, angle):
    duty = 2.5 + (angle / 180.0) * 10
    pwm.ChangeDutyCycle(duty)
    time.sleep(0.5)
    pwm.ChangeDutyCycle(0)  # Stop sending signal to prevent jitter

try:
    print("Setting all servos to 90°...")
    for pwm in pwms:
        set_servo_angle(pwm, 90)
    print("Done.")

except KeyboardInterrupt:
    print("\nStopped by user.")

finally:
    for pwm in pwms:
        pwm.stop()
    GPIO.cleanup()
