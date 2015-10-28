# Wireless Head Tracker calibration and configuration #

The calibration and configuration of the WHT can be performed with the WHTConfig.exe program. The program is included in the WHT softwate package and you can get it here: https://docs.google.com/uc?authuser=0&id=0B5QsMM8GX6NEV01oVFdwOVRJS3M&export=download

Download it and unpack it into a new folder.

### Basic calibration ###

  1. Plug the USB dongle into your PC and turn on the tracker.
  1. Start the WHTConfig.exe program. You should see this ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/wht_config.png](http://wireless-head-tracker.googlecode.com/svn/wiki/images/wht_config.png)
  1. Make sure the "RF packets" field in the status bar of the window is above 80%. This is a measure of quality of the radio connection. If it's lower than 80% bring the tracker closer to the dongle.
  1. Place the tracker on a flat surface, then press the _Calibrate_ button in the WHTConfig program
  1. A yellow light should light up on the tracker. Wait for it to go off.
  1. The calibration is complete.

### Yaw drift compensation ###

Rough compensation calculation:

  1. Place the tracker on a flat surface
  1. Press the Reset button on the WHTConfig program
  1. Let the tracker rest for about 15 minutes. Do not move the tracker.
  1. Press the Save button on the WHTConfig program
  1. Yaw drift is now compensated

Fine tuning:

  1. In WHTConfig select Auto-center _Off_ and press _Save axes setup_
  1. Put the tracker on your head and start playing.
  1. During play do not press the reset button on the tracker or the Reset button in WHTConfig
  1. If you notice the yaw heading (left/right) has drifted significantly into either direction, go to WHTConfig look straight ahead and press _Save_
  1. Repeat the last step until you can not notice a drift for 10-15 minutes of use.
  1. In WHTConfig select Auto-center _Medium_
  1. The tracker should not drift any more after this