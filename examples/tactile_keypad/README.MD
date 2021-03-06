## Using the Cthulhu Shield and Arduino Uno to Send Keystrokes With Your Tongue!

# Introduction:

The Cthulhu Shield and electrode array can be used to sense whether or not your tongue is in contact with certain electrodes. Combined with the electrotactile ability of the Cthulhu Shield, this can be used to create 'virtual' tactile buttons that can be pressed with the tongue. With some minor software hacking of the Arduino, we can get the Arduino-Cthulhu to tell the computer that it is a keyboard and send keystrokes to your computer with your tongue.

This example will show you how to upload the example 'tactile_keypad.ino' sketch to an Arduino Uno with mounted Cthulhu Shield (and then hack the Arduino) to  use your tongue to send 'w''a''s''d' and 'space' keystrokes to your computer. These keys are the standard keys used to control character movement in many PC games, thus you will be able to move your character with your tongue as shown in the gif below.

![Game_Control](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/GameControlGif.gif?raw=true)

# Required Materials:

* Cthulhu Shield

![Cthulhu Shield](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/cthulhusmall.jpg?raw=true)
* Arduino Uno or Mega or compatible clone with Atmega16U2 as USB to UART converter (it sounds like older boards using the Atmega8U2 may also work)

![Cthulhu Shield](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/unosmall.jpg?raw=true)
* USB A to B Cable

![USB A to B Cable](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/usbsmall.jpg?raw=true)

* One 18 Channel flexible electrode array from Sapien LLC

![Cthulhu Shield](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/ribbonsmall.jpg?raw=true)

# Required Software:
* This library
* [Arduino IDE](https://www.arduino.cc/en/Main/Software)
* [Flip programmer](https://www.microchip.com/developmenttools/ProductDetails/flip)


# Hardware Assembly:
Install Cthulhu Shield onto Arduino Uno or Arduino Mega and attach the USB cable and electrode array. 

# Example:
Open Arduino IDE. Once you have installed the Cthulhu Shield library (see 'Install Library' at end) go to **file**>**examples**>**Cthulhu-master** and open the **tactile_keypad** example sketch.

![example](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/arduino_tactile_keypad_example.jpg?raw=true)

Set your board and serial port from the **tools** dropdown menu and upload the sketch to your Arduino Uno or Mega.

![example](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/arduino_brdselect_uno.jpg?raw=true)

![example](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/arduino_comselect.jpg?raw=true)

![example](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/arduino_upload.jpg?raw=true)



Once you have downloaded the [Flip programmer](https://www.microchip.com/developmenttools/ProductDetails/flip), open the progam and select the ATmega16U2 device by selecting the IC icon in the upper left of the window. 

![flipchipselect](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/flipchipselect.jpg?raw=true)

With the Arduino powered, momentarily short these two pins together with a screwdriver or something metallic to put the ATmega16U2 into a state that allows to reprogram it.

![Unohack](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/unokeyboardhack.jpg?raw=true)

Click the USB cable icon in the upper left and select the 'USB' option from the dropdown. 

![USB](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/select_USB.jpg?raw=true)

Previously 'greyed-out' features in the window should now be available (if you can't connect and get an error message see section below titled 'Troubleshooting-Update Driver')

Select the Load HEX file button at the top of the window and navigate to and select the 'Arduino-keyboard-0.3.hex' file on your computer (located in the '16u2_firmware' folder of this example)

![load hex](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/firmwareselect.jpg?raw=true)

Once the firmware is selected, hit run to upload the new firmware to the ATmega16U2 chip on the Arduino.

![run](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/uploadfirmware.jpg?raw=true)

**Now unplug your Arduino from your computer to remove power and plug it back in again. Your computer should now recognize the arduino as a standard keyboard.**

If you havent already, carefully lift the latch of the ZIF connector, insert the electrode array gold side down, and close the latch. Open a text editor and place the electrode array in your mouth to test it out. 

Use the tip of your tongue to press the tactile 'buttons' on the electrodes at the front, back , and both sides of the array. The LED's on the Cthulhu Shield will change brightness when your tongue is contacting them, so look at them and move your tongue around to train up and practice. 'w', 'a', 's', and 'd' keystrokes are mapped to the front, left, back, and right electrodes respectively. A 'space' keystroke can be sent by flattening your tongue against the array and pressing all the electrodes simultaneously. 

When you feel like it, fire up your favorite game with 'wasd' motion control and try controlling your character with your tongue!


**Note: If you want your Arduino to act like a regular Arduino again (so you can load different sketches on it) you must short the pins together and repeat this process, selecting 'Arduino-usbserial-uno.hex' or 'Arduino-subserial-mega.hex'to put the standard Arduino firmware back onto the ATmega16U2.**



# Going Further:

Change the keystrokes used in the example to something that you prefer! Maybe you want to hotkey certain actions to your tongue to give you an edge while gaming. If you have a disability, maybe there are other keystrokes that suit your needs better! 

Have fun, and if you make something cool, share it with us!

# Acknowledgments: 
Inspiration for this project and Firmware for Atmega16U2 came directly from coopermaa at https://github.com/coopermaa/USBKeyboard










# Troubleshooting-Update Driver:
If you get an error message when trying to connect to your device in Flip, you may need to update the driver in your device manager. 

Make sure you are running java Runtime Environment 32, then go to **device manager** on your computer, find the 16U2 device, 

![16U2device](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/driverupdate1.jpg?raw=true)

right click and select **properties** > **update drivers**, **browse my computer for driver software** and navigate to and select the **Flip folder** on your computer. 

![16U2device2](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/driverupdate2.jpg?raw=true)

![16U2device2](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/driverupdate3.jpg?raw=true)

![16U2device2](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/driverupdate4.jpg?raw=true)

Once the **Flip folder** has been selected, click **update drivers**.

![16U2device2](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/driverupdate5.jpg?raw=true)


# Install Library:

Right now, the easiest way to install the Cthulhu library is by downloading the Zip file from github, and manually adding it from the arduino 'sketch' dropdown menu.

Navigate to the Cthulhu repo main page and download the zip file.

![zip](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/download_zip.jpg?raw=true)

Open Arduino and select **Include Library** > **Add .ZIP Library** from the **Sketch** dropdown menu.

![add library](https://github.com/SapienLLCdev/Cthulhu/blob/master/jpgs/arduino_add_zip_library.jpg?raw=true)

Navigate to the zip file you downloaded and select it (probably your 'Downloads' folder). 

The library should now be installed. 
