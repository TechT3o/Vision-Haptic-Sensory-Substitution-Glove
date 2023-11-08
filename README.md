# Haptic_depth_sensing_glove

Haptic feedback glove device that uses a motor camera and mini motor disks to help visually impaired people understand the 3d space around them.

The idea is to mount a small camera on the palm of the visually impaired user, construct the depth map and perform sensory substituition of vision by using a high resolution haptic feedback gloved comprised of an array of mini DC motor disksto assign a different intensity in the direction where the user's hand is pointing at, analogous to how close the object is.

The goal is for the user to be able to identify what type of object their hand is pointing at for object recognition and object fetching and for the user to be able to do wayfinding and navigate in a room using the device.

User studies that examine the usability (Learnability, Efficiency, Memorability, Errors, Satisfaction) and effectiveness of the device will be done.

# Hardware

1x [Arduino Nano BLE sense 33](https://docs.arduino.cc/hardware/nano-33-ble-sense)
1x [OV7670 camera module](https://www.openhacks.com/uploadsproductos/ov7670_cmos_camera_module_revc_ds.pdf)
20x [Mini motor disk](https://www.adafruit.com/product/1201#technical-details)
20x [p2n222A npn transistor](https://www.onsemi.com/pdf/datasheet/p2n2222a-d.pdf)
20x 30 Ohms resistors
20x 2.2k Ohms resistors
20x 33 pF capacitors
20x 1N4001 diode
20x motor circuit PCBs - see file

## Motor driver circuit

The mini disk motors require around 100 mA of current in order to rotate at full speed with 5V power. The Arduino output pins can provide up to 10 mA, therefore we need a driver circuit to be able to power the motor using a PWM signal. The circuit shown in Figure was build. It uses an npn transistor whose base is connected to the GPIO output pin of the Arduino. When the PWM signal gets applied to the base of the transistor the Collector Emitter channel opens and current from the VCC flows through the disk motor and makes it spin with intensity analogous to the PWM signal. The resistor R2 limits the current flowing through the disk motor. A value of 30 Ohms was selected as 5V/30 = 166 mA max current that could flow through R1 ignoring rest of circuit resistances. R2 was also selected to limit the base current. As the base current is very small values of up to 5k could be selected but the chosen value for R1 in this project was 2.2k Ohms. The capacitor is used to soften voltage spikes from the motor's rotation and a diode is put to prevent a voltage spike to flow through the motor.

Figure 1
![image](https://github.com/TechT3o/Haptic_depth_sensing_glove/assets/87833804/c52ca1bd-b7f3-442d-acfb-adf6d63f25e5)

The PCB of this circuit shown in Figure was made and the Gerber files were sent to [SOHPARK](https://oshpark.com/) for manufacturing.

Figure 2
![image](https://github.com/TechT3o/Haptic_depth_sensing_glove/assets/87833804/0849f1bc-9bf5-438c-accb-9387e1dbf27c)

The received PCBs arrived and the components were soldered on top of it with the disk motors attached to the back of the PCB.

Figure 3
Figure 4

## Depth Estimation

In order to 



