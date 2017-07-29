1. Download [Arduino IDE](https://www.arduino.cc/en/Main/Software).  
2. Open [this code](https://github.com/michalmonday/supremeDuck/blob/master/source/bluetooth%20customization/btSerial.ino) in Arduino IDE.   
3. Pick: "Tools -> Board -> Arduino Leonardo".  
4. Make sure the device is connected to PC and pick: "Tools -> Port -> COM X (Arduino Leonardo)".  
5. Upload the code by clicking the "Upload" button in the top left corner.  
6. Open serial monitor by going to: "Tools -> Serial Monitor". (You might have to pick "Tools -> Port -> COM X (Arduino Leonardo)" again after the upload)  
7. Choose "No new line" and "9600 baud" in the bottom left corner of the serial monitor.  
8. Input the following three commands in the serial monitor text box at the top of it:  
    AT  
    AT+NAMEmyName  
    AT+PIN1234  
The first command should output "OK" message to the serial monitor main area, the second should output "OKsetname", the third should output "OKsetPIN". If that's the output then the name of the device has been successfully changed to "myName" and the pin to "1234".  
9. Upload the [original supremeDuck](https://github.com/michalmonday/supremeDuck/blob/master/source/supremeDuck.ino) code the same way and it's done.  

The whole process is presented in the following video:  
[Video presentation](https://www.youtube.com/watch?v=KsuUSxYfdU8&index=4&list=PLnVVAaZSdNGtcMunS1_Wy3smTZLlzIaV2)




