**Brief description:**  
Thanks to it the device will work with any language setting on the target PC. (works on Windows only)


**Explanation:**  
The MultiLang method is a method relying on the very useful feature of Windows. Windows allows the user to hold "alt" key and input ASCII value of a character using the numpad. Taking advantage of this feature it is possible to type special characters regardless of the language setting on the PC.

> Keyboard simulating devices work differently depending on the system language setting. At the moment (25/7/17) the original HAK5 "rubber ducky", "Malduino" and other arduino based HID projects require the user to pick a keyboard language setting before uploading the code. It means that device has to be re-programmed before using it with different PCs if they have different language settings. That's not the case with supremeDuck, it handles the aforementioned problem in 2 ways:
>   1. It gives an ability to dynamically change the desired language settings by using the android app whenever needed (the device must be turned on while changing it, it's called "Keyboard language encoding" in the categories list). 
>   2. It takes advantage of the fact that Windows allows a tricky method of typing characters (by using ALT + NUMPAD keys it is possible to type the ASCII code and the desired character will be typed). As a result the device can be set to work with all of the most frequently used language settings without the need to change anything (as long as it's used on Windows). In the options of the android app it's possible to dynamically enable and disable it (it's called "MultiLang - Windows only" in the categories list).

**Presentation:**  
[MultiLang method presentation](https://youtu.be/Sk2NfTLyEGM)  
[Presentation of encoding adapted from HAK5 encoder - without MultiLang](https://www.youtube.com/watch?v=4nbv-LyDWvk)  

The MultiLang method seems flawless in compatison with the encoding method adapted from the HAK5 rubber duckys' encoder which doesn't provide 100% reliability in all languages.