#import pin library
from machine import Pin
#include the servo library
from servo import Servo
#include time library
import time

#define the pins for 4 button switches
switchM1left=Pin(15,Pin.IN,Pin.PULL_UP)  #Pin.PULL_UP is used when you remove the resistor completely (circuit is only with two wires now)
switchM1right=Pin(4,Pin.IN,Pin.PULL_UP)
switchM2left=Pin(18,Pin.IN,Pin.PULL_UP)
switchM2right=Pin(19,Pin.IN,Pin.PULL_UP)

#define the pin to be an output
#Servo is an output device
servo1_pin=Pin(21, Pin.OUT)
servo2_pin=Pin(23, Pin.OUT)

#initialise the servo for use
Myservo1=Servo(servo1_pin)
Myservo2=Servo(servo2_pin)
angle1=90
angle2=90
Myservo1.write_angle(angle1)
Myservo2.write_angle(angle2)

while(1):
    switchstateM1left=switchM1left.value()
    if(switchstateM1left==0):
        #write the angle to servo
        angle1=angle1-3
        if angle1<0:
            angle1=0
        Myservo1.write_angle(angle1)
    switchstateM1right=switchM1right.value()
    if(switchstateM1right==0):
        #write the angle to servo
        angle1=angle1+3
        if angle1>180:
            angle1=180
        Myservo1.write_angle(angle1)
    switchstateM2left=switchM2left.value()
    if(switchstateM2left==0):
        #write the angle to servo
        angle2=angle2-3
        if angle2<0:
            angle2=0
        Myservo2.write_angle(angle2)
    switchstateM2right=switchM2right.value()
    if(switchstateM2right==0):
        #write the angle to servo
        angle2=angle2+3
        if angle2>180:
            angle2=180
        Myservo2.write_angle(angle2)
    time.sleep(0.1)
        
    
    
    
    

            
