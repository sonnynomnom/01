# 01


```from time import sleep
import RPi.GPIO as GPIO # import Raspberry Pi GPIO library
import random

####### STRING -> BINARY ######

str = "hello world"
print("TEXT: " + str)
sleep(2)

binary = ' '.join(format(ord(x), 'b') for x in str)
print("BINARY: " + binary)
sleep(2)

GPIO.setmode(GPIO.BCM)

solenoid_pin = 18

solenoid_pin2 = 12

# GPIO.setup(6, GPIO.IN)
GPIO.setup(solenoid_pin, GPIO.OUT)
# GPIO.setup(led, GPIO.OUT)
GPIO.setup(solenoid_pin2, GPIO.OUT)

print("Starting...")
sleep(1)
print("3...")
sleep(1)
print("2...")
sleep(1)
print("1...")
sleep(1)




########### 0s and 1s ###################

try:
    # sleep(1) # stabilize
    
    # while True:
    
    for blah in range(len(binary)):
        
#        for x in range(5): # wait 5 sec
#            sleep(1)
#            print(x)
        if (binary[blah] == '1'):
          GPIO.output(solenoid_pin, GPIO.HIGH)
          print("Valve 1 OPEN.")
          sleep(0.5)
          GPIO.output(solenoid_pin, GPIO.LOW)
          print("Valve 1 CLOSED.")

    
        elif (binary[blah] == '0'):
        
          GPIO.output(solenoid_pin2, GPIO.HIGH)
          print("Valve 2 OPEN.")
          sleep(0.5)
          GPIO.output(solenoid_pin2, GPIO.LOW)
          print("Valve 2 CLOSED.")
        
#        for x in range(5): # wait 5 sec
#            sleep(1)
#            print(x)
#            
        # different timing so it sounds like human typing
        
        for x in range(random.randint(0, 4)):
            sleep(1)
            print("waiting... ")
            
except KeyboardInterrupt:
    pass
finally:
    GPIO.cleanup()

```


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
