#include <Servo.h>

/* ---- Sensor Pin Define ----*/
int Sensor_1 = A0;  // Input pin for first EMG sensor (Hand control)
int threshold_1 = 200;  // Threshold value to trigger hand closing
int Sensor_2 = A1;  // Input pin for second EMG sensor (Arm control)
int threshold_2 = 200;  // Threshold value to trigger arm movement

/* ---- Variable Storage ---- */
int emgValue_1 = 0;
int emgValue_2 = 0;

/* ---- Servo Object Initialization Controlling 5 fingers, wrist, and elbow ---- */
Servo thumb, index, middle, ring, pinky, wrist, elbow;

void setup()
{
/* ---- Attach servos to their respective digital PWM pins ---- */
 thumb.attach(3);
 index.attach(5);
 middle.attach(6);
 ring.attach(9);
 pinky.attach(10);
 wrist.attach(11);
 elbow.attach(12);
}

void loop()
{
/* ---- Hand Control Logic ---- */
 emgValue_1 = analogRead(Sensor_1);  // Read EMG sensor 1
 if (emgValue_1 > threshold_1)
{
 closeHand();  // Flex all fingers if signal is strong
}
 else
{
 openHand();  // Relax all fingers otherwise
}

/* ---- Arm Control Logic ---- */
emgValue_2 = analogRead(Sensor_2);  // Read EMG sensor 2
 if (emgValue_2 > threshold_2)
{
 Move();  // Rotate wrist and elbow if signal is strong
}
 else
{
 Stop();  // Return arm to rest positio
}

delay(3000);  // Wait 3 seconds before next reading
}


/* ---- Helper Functions ---- */

void openHand()
{
/* ---- Set all finger servos to 0 degrees (Open) ---- */
 thumb.write(0);
 index.write(0);
middle.write(0);
 ring.write(0);
pinky.write(0);
}

void closeHand()
{
/* ---- Set all finger servos to 180 degrees (Closed) ---- */
 thumb.write(180);
 index.write(180);
 middle.write(180);
 ring.write(180);
 pinky.write(180);
}

void Stop()
{
/* ---- Set Arm to rest position ---- */
 wrist.write(180);
 elbow.write(0);
}

void Move()
{
/* ---- Activate Arm movement ---- */
 wrist.write(90);
 elbow.write(180);
}
