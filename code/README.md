There are two folders in this project:

1. **The first folder** is used to check the working of the bot.  
   It contains testing scripts to:
   - Verify if the servo motors can rotate 180 degrees (`0-180_check.py`), since some may be defective and only rotate ~90 degrees.
   - Check if the bot tilts properly in all directions (`direction_check.py`).
   - Set the initial angles of the servos (`set_initial_angle.py`).  
     → In this setup, the 0° angle is defined as pointing towards the ground.

2. **The second folder** contains the main code to run the actual ball-balancing system.
