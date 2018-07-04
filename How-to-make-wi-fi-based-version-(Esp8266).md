### 1. Get/assemble the hardware. See this [github page](https://github.com/spacehuhn/wifi_ducky) or this [video](https://www.youtube.com/watch?v=Utq4C9S3-uI) to see how to do that. Different boards/modules can be used for it, but the hardware must have: 
 
A board with Atmega32U4 such as:
- Arduino Pro Micro 5V (with external 3.3V regulator or two 3.6V zener diodes)  
- Arduino Pro Micro 3.3V (requires [Sparkfun plugin](https://learn.sparkfun.com/tutorials/pro-micro--fio-v3-hookup-guide/installing-windows))
- CJMCU Beetle (with external 3.3V regulator or two 3.6V zener diodes)  
- SS Micro  
- Arduino Leonardo  

A board with Esp8266 module such as:  
- Esp8266 12-F  
- NodeMCU (most of the steps listed below are not applying to it because it can be flashed much more easily, all you have to do with is to upload [Esp8266.ino]() to it using Arduino IDE, there are many guides on how to do that) 

Both modules (Atmega32U4 + Esp8266) should be connected together as shown in the wifi_ducky project. Make sure that the GPIO 0 pin of Esp8266 is connected to ground, it is necessary to flash Esp8266 with new code, after the flashing process is done it should be disconnected.

### 2. Upload the code below to your chosen Atmega32U4 board using Arduino IDE:  
```cpp
// taken from: https://gist.github.com/spacehuhn/b2b7d897550bc07b26da8464fa7f4b36

void setup()
{
  Serial1.begin(115200);
  Serial.begin(115200);
}

void loop()
{
  while(Serial1.available()){
    Serial.write((uint8_t)Serial1.read());
  }

  if(Serial.available()){
    while(Serial.available()){
      Serial1.write((uint8_t)Serial.read());
    }
  }
} 
```
Choose Tools -> Board -> Arduino Leonardo (for all boards except Arduino Pro Micro 3.3V which requires Sparkfun plugin)

### 3. Download Esp8266Flasher program ([32-bit](https://github.com/nodemcu/nodemcu-flasher/tree/master/Win32/Release), [64-bit](https://github.com/nodemcu/nodemcu-flasher/tree/master/Win64/Release)).
The code uploaded in step 2 will make sure that the Esp8266 code uploaded using this program will reach Esp8266 even that it's not directly connected to PC (it's connected through the board with Atmega32U4).

### 4. Open the Esp8266Flasher program, load this [bin file]() and flash it.
Pick the COM port corresponding to the connected device.  
Press `Config` and click on the cog icon to load the file, check the corresponding checkbox and uncheck others. Use `0x00000` offset.  
Press `Advanced` and select `115200` Baudrate, `4MByte` Flash size, `80MHz` Flash speed and `DIO` SPI Mode.  
Press `Operation` and finally press `Flash(F)`  

### 5. Open the main supremeDuck code in Arduino IDE, uncomment line shown below and upload the code.  
The line to uncomment is:
```cpp
//#define USE_TX_RX_PINS
```
It should look like this after uncommenting:
```cpp
#define USE_TX_RX_PINS
```
Pick Tools -> Boards -> Arduino Leonardo (exception for Arduino Pro Micro 3.3V)

### 6. Disconnect GPIO 0 (Esp8266) from ground.
The whole process is slightly complicated so I tried to keep it as simple as possible but there are few ways it could be done in more convenient way. For example:
- a switch between GPIO 0 and ground could be used
- as shown in the esp flasher code [here](https://gist.github.com/spacehuhn/b2b7d897550bc07b26da8464fa7f4b36) digital output pins could be used to determine GPIO 0 state, this would require more wiring work but would save time attaching/detaching GPIO 0 to GND over and over again

### 7. The device should be in working order now.
Let me know on discord (michalmonday#3687) if you encounter any problems while following this guide.
