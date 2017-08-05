# List of contents: 
* [Prerequisites](#prerequisites)
* [Hardware setup](#hardware-setup)
* [Software setup (Arduino)](#software-arduino)
* [Software setup (app) - option 1](#software-app)
* [Software setup (app) - option 2](#software-app---alternative-installation-from-source)


***


# Prerequisites 
* Arduino Pro Micro 5V 16Mhz (8Mhz version would get damaged without additional plugin. Take a look at product description for "Supported under Arduino IDE v1.0.2" which means that the device may not work without reflashing. Pick those with v1.05 support instead. I personally recommend [this seller](http://www.ebay.co.uk/usr/scooterboy101), gives outstanding support and has good knowledge about these devices.)
* bluetooth module HC-06
* 2K Ohm resistor
* 4.7K Ohm resistor (tested and working with 5.1k too)
* USB OTG adapter + optionally USB type A connector
* solid core wire
* soldering equipment
* hot glue gun
* heatshrink



# Hardware setup
1. Make sure to have all prerequisites. 
2. Desolder and remove pins from the bluetooth module. It may be difficult to desolder them all at once, I used pliers and gentle rotational movements to destroy the black plastic which holds them together and removed them separately. 
> It's a good idea to get rid of the solder inside the pins so it's possible to put the cables through the pins before soldering. It makes the soldering much easier.
3. Hot glue the Arduino and bluetooth boads together (chips pointing outwards) 
4. Cut a 6cm piece of wire, cut 1 "leg" of each resistor (2k and 4.7k) and create voltage divider by soldering all 3 together. 
5. Cut wire into 3x6cm pieces, strip the rubber from their ends and solder them accordingly to the pattern presented on the images.
> Personally I like to put all the cables inside the pins and bend them before soldering. It's shown at the images below.
6. Connect the device to PC, it should be [blinking](https://youtu.be/ZgmhzojPXA4)
7. Optionally the USB type A connector could be soldered to the USB OTG adapter and stabilized with hot glue as displayed on the pictures below.
> By wiping the hot glue with a finger you could get rid of the hot glue excess (the connector at the bottom of the picture had its glue "wiped" so it's not so bulky unlike the other two connectors above it). Pictures don't show it clearly but the hot glue is also added on the other side of the connectors.

![](http://i.imgur.com/rwbGNvQ.jpg)

![](http://i.imgur.com/GhOuCLn.png)

![](http://i.imgur.com/F3n9h1s.jpg)

![](http://i.imgur.com/vqzpYiD.jpg)

![](http://i.imgur.com/mnR4kfK.jpg)

![](http://i.imgur.com/QPFaG62.jpg)

![](http://i.imgur.com/wjSBxaS.jpg)


# Software (Arduino) 
1. Download [Arduino IDE](https://www.arduino.cc/en/main/software) and [Arduino sketch](https://github.com/michalmonday/supremeDuck/blob/master/source/supremeDuck.ino).
2. Open arduino IDE. Click on Tools -> Board -> **Arduino Leonardo (Important - incorrect setting of the board may require [reflashing](http://forum.arduino.cc/index.php?topic=376079.0) the arduino or performing a [tricky reset](https://www.youtube.com/watch?v=dFQHXm1y5Io).** Click on Tools -> Port -> COM X. Paste [this sketch](https://github.com/michalmonday/supremeDuck/blob/master/source/bluetooth%20customization/btSerial.ino) and upload it to the board.
3. Open Tools -> Serial Monitor, the new window will popup, select "No line ending" and "9600 baud" at the bottom corner of it. Then input the following commands into the input box located at the top:
AT+NAMEyourname
AT+PIN1234
> The commands and the script mentioned above will set the name of the bluetooth module to "yourname" and its pin to "1234". Note that the pin has to consist of 4 digits. If everything goes right you should get "OKsetname" and "OKsetpin" responses.
4. Upload the main sketch.

![](http://i.imgur.com/EKH4JhM.png)

![](http://i.imgur.com/AFmjLLG.png)



# Software (app)
Install the app on your mobile from the [Google Play Store](https://play.google.com/store/apps/details?id=appinventor.ai_michalmonday17.supremeDuck)

# Software (app) - alternative installation from source
1.Download MIT project to your PC. Then download [MIT App Inventor 2 Companion](https://play.google.com/store/apps/details?id=edu.mit.appinventor.aicompanion3&hl=en_GB) to your android.  
2. Register at MIT app inventor website, log into it and import the [MIT project](https://github.com/michalmonday/supremeDuck/blob/master/source/supremeDuck.aia) (Connect -> Import project .aia). I recommend to watch [this tutorial](https://www.youtube.com/watch?v=o-YVvxYiSuk) which explains how to create and manage applications made using this tool.  
3. Click on Build -> App (provide QR code for .apk). The QR code will appear, it has to be scanned with a smartphone. Open your MIT AI2 Companion app on android and press scan QR code which will should appear on the screen of your PC. 
> This step isn't necessary to test and develop the application, MIT provides comfortable quick update system which automatically lets the user to preview application while changing its components. If you'd like to modify the source then instead of clicking on "Build" click on "Connect -> AI Companion" instead and also scan the QR code but this time it will show preview of the app on your mobile and respond in real-time to any changes you make using MIT App inventor 2.
4. Complete the installation process and the project should be functional.

![](http://i.imgur.com/O2RVH0X.png)

![](http://i.imgur.com/Hz8uInl.png)

![](http://i.imgur.com/Pjwmz56.png)

