# RPI4-TM1637
tutorial on how to connect the TM1637 7seg display to read CPU temps of a raspberry pi 4

# **TM1637 CPU TEMPERATURE DISPLAY**

 **HOW TO USE**
run `pip3 install raspberrypi-tm1637` to download the librarys.
make a new python script and copy this code to the file:

```
  import tm1637 #import tm1637 module

  import os
  import time

  TM = tm1637.TM1637(clk=21, dio=20) # Set the GPIO pins

  while True:
     temp = os.popen("vcgencmd measure_temp").readline() # Reads the CPU temperature from the raspberry pi

     temp_num = int(float(temp.replace("temp=","").replace("'C\n",""))) # Convert the temperature into an integer
     TM.temperature(temp_num) # Print the temperature to the TM1637 display

     time.sleep(2) #Wait 2 Seconds```
