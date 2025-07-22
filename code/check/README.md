## 🔧 Utility Scripts

These helper Python files assist in testing and calibrating your ball-balancing platform:

### `0-180_check.py`
- **Purpose**: Test if your servo motors can rotate the full 180° range.
- **Why**: Some servos are defective and can only rotate ~90°. This test helps identify such units before using them in the system.

### `direction_check.py`
- **Purpose**: Verifies that the platform tilts correctly in all directions.
- **Why**: Ensures that servo wiring, orientation, and inverse kinematics calculations are working as expected.

### `set_initial_angle.py`
- **Purpose**: Calibrates the starting (equilibrium) angle of each servo.
- **Note**: In this setup, the 0° angle is defined as fully downward (i.e., servo arm pointing toward the ground).
- **Use**: Run this script before first-time use or after reassembly to ensure consistent starting angles.

---

### ✅ Recommended Workflow

1. Run `0-180_check.py` to confirm full servo motion range.
2. Run `set_initial_angle.py` to position all servos to a known, consistent downward orientation.
3. Run `direction_check.py` to ensure your platform responds correctly to tilt commands in all directions.

