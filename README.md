# EK691 Practicum
RPi sensor (tested on B+ model only, 1st gen)

You need a Plotly and Twilio account, and a webpage that has these APIs embedded. (Something as simple as a blogspot page will work, just throw in the embedding HTML). This version does not have a properly functioning webcam, but a cam can be connected  on the board and managed on the same .py script.

Hook up an infrared sensor to the GPIO ins, as well as ground/5V; this depends if you have an advanced layout with an ADC or just a straight connection to an analog IR sensor.

lastscrumdemo.py needs to be edited with the appropriate phone#'s for the twilio feautre, and possibly ssh keys for the hosting webpage.

Afterward, save RPi/lastscrumdemo.py on an RPi and automate with the following on the board (tested only on Jessie Raspbian):
#
1. Edit /etc/inittab; comment out 1:2345:respawn:/sbin/getty 115200 tty1
2. Replace with 1:2345:respawn:/bin/login -f pi tty1 </dev/tty1 >/dev/tty1 2>&1
3. Edit /etc/profile; add at the bottom of the script: sudo python /directory/of/your/pythonscript.py
4. You can add a board timeout/shutdown in /etc/profile or in your .py script, depending on what you want.
5. Restart the  RPi and open your webpage; it may take a few minutes for readings to register. Wave your hand in front of the sensor to test and see if there is any response from the IR sensor. Depending on the simplicity of your sensor/circuit, you may have a shorter detectable range.

#----------------------------------
#Thanks to Adafruit for RPi instructions and MCP reference
https://learn.adafruit.com/adafruitsraspberrypilesson4gpiosetup/adafruitpicode

#Thanks to Jeremy Blythe for additional MCP reference
https://github.com/jerbly/Pi

#----------------------------------
#Plotly API from

https://plot.ly/python/gettingstarted/

#----------------------------------
#Twilio SMS messaging Python API from

https://www.twilio.com/docs/python/install
