# 01
asdf

from time import sleep
import RPi.GPIO as GPIO # import Raspberry Pi GPIO library

#import random

GPIO.setmode(GPIO.BCM)

solenoid_pin = 18

#GPIO.setup(6, GPIO.IN)
GPIO.setup(solenoid_pin, GPIO.OUT)
#GPIO.setup(led, GPIO.OUT)

try:
    sleep(1) #stabilize
    while True:
        for x in range(5): #wait 5 sec
            sleep(1)
            print(x)
    
        GPIO.output(solenoid_pin, GPIO.HIGH)
        print("Valve OPEN.")

        for x in range(5): #wait 5 sec
            sleep(1)
            print(x)

        GPIO.output(solenoid_pin, GPIO.LOW)
        print("Valve CLOSED.")

        for x in range(5): # wait 5 sec
            sleep(1)
            print(x)
except KeyboardInterrupt:
    pass
finally:
    GPIO.cleanup()
