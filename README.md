# Thames : WVR in a Pedal

Thames is an open-source midi instrument. It comes pre-loaded with some instruments, but it's easy to make your own too. You can even setup what the buttons and encoder do, and control the LEDs, by writting some custom Arduino code.  
Join us on the WVR Forum : https://groups.google.com/g/wvr-audio  

# Power
Thames takes between 6 and 9 VDC, with a center-negative PSU. Boss pedal style PSUs work perfectly.

<img src="https://github.com/marchingband/wvr_thames/blob/main/images/IMG_3453.jpeg?raw=true" width="50%" height="50%">

# USB MIDI
Connect to any USB MIDI controller. WVR will power the controller.

<img src="https://github.com/marchingband/wvr_thames/blob/main/images/IMG_3452.jpeg?raw=true" width="50%" height="50%">

# MIDI
Using a "TYPE B" 1/8" TRS midi cable

# Headphones
Connect any headphones to the 1/8" stereo output. This output is not properly driven for headphones, so the output may be quiet, or may be slightly disptorted, depending on what headphones you use. It usually sounds pretty great though!

# Line out
Connect any line level device to the 1/4" outputs, or to the 1/8" stereo outputs.

<img src="https://github.com/marchingband/wvr_thames/blob/main/images/IMG_3451.jpeg?raw=true" width="50%" height="50%">

# Operation

<img src="https://github.com/marchingband/wvr_thames/blob/main/images/IMG_3450.jpeg?raw=true" width="50%" height="50%">

The LEDs display the volume by default. The volume is a number from 0 to 127. The LEDs will fade to display the volume. Turning the encoder changes the volume. The volume always starts at the `global volume` value which is set in the UI. The default global volume is 96 (3/4 of max).

When you press the Encoder, the LEDs now display the voice number currently selected. Turning the encoder while pressed will change the voice. The LEDs display the voice number in MSB format binary. There are 4 LEDs, which in binary can display numbers from 0 to 15.
```
0 = 0000
1 = 1000
2 = 0100
3 = 1100
...etc
```
There are 4 pre-programmed voices:  
0 -> Wurlitzer  
1 -> Drum Kit  
2 -> Drum Machine A  
3 -> Drum Machine B  

Voices 0 and 1 are multi-sampled, 2 and 3 are not.

Voices 0 and 1 have functions assigned to the buttons, 2 and 3 do not.
```
Voice          Button A          Button B
------------------------------------------
  0            Dampen            Sustain
  1            HiHat Control     Kick Drum
```

All the power of the WVR platform is available in the Thames as well, you just need to connect to it over WIFI.  
To turn on the WIFI:  
1) unplug the power to Thames
2) hold down Button A
3) plug power into Thames
4) wait 4 or 5 seconds untill the LEDs blink 5 times  

On a computer or mobile device, connect to the WVR wifi network, using the password "12345678".  
Open a web browser (Chrome is best) and navigate to http://192.168.5.18/, and the WVR UI will open.  

# Trouble Shooting
There is one known hardware bug in Thames. Sometimes the encoder sticks in a 1/2 rotational position, and if the Thames is powered on while this is the case, it triggers a special bootloader mode in the ESP32, and the Thames firmware will not boot, and the pedal will not work. You will know this has happened because **only LED #3 will light up**. The fix is to simply twiddle the encoder a bit, then turn the Thames off and on again by unplugging, and then pluggin in.  

Thames WIFI only works while the pedal is very close to the computer? The power of the Wifi Radio on ESP32 can be controlled. By default, the Thames has the power set to the absolute minimum. This means that the wifi range is just a few feet. If you want to change this, the `wifi radio power` can be changed in the UI, in the main `WVR` menu. Next time WVR boots, it will set the new wifi radio power. More WiFi radio power means more power is used, which means more heat will be generated by the LDO, and more power is pulled from your PSU. At low WiFi power, Thames draws about 2W at 9V, at high WiFi power it draws about 3W.

# Recovery Mode
All WVR devices have a special Recovery Mode. This is useful for any time you are changing settings, or flashing custom Arduino code, and for whatever reason, you are unable to connect the WVR network. To activate Recovery Mode on the Thames:  
1) unplug power to Thames
2) hold down Button B
3) plug in power to Thames
4) wait 4 or 5 seconds untill just LED 3 is lit.  

Now WVR is in Recovery Mode, any additional firmware will not boot, the wifi will always launch, and it will serve a special Recovery Mode UI.

# Features
If you have an idea for a feature that you would like to see implemented for Thames, feel free to request it! Create an ISSUE in the menu at the top of this page, and desribe the feature. If you don't use GitHub, you could also join the WVR_AUDIO forum and descrive the feature request there. I will respond ASAP, and if it seems like something others would enjoy, then I will do my best to make it happen!  
WVR can store up to 10 firmwares, and so can your Thames. It's exciting to imagine a Thames pedal with multiple different firmwares which do various things, all saved in a pedal :)
