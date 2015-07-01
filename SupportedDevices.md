# Introduction #

The audio driver is now based on a method that is a little bit more official (using java api).
So it should now work on almost all devices.

However there is some restrictions :

# Known incompatibility #
  * Some armv4 based devices - If you own an armv4t device and want to help us to support it, please send us the "device" name : install an application such as DeviceInfo to get this information (that's a string that allow to determine which device it's exactly).

# There is also some audio routing issues #
It can produce echo if routed to rear speaker or no sound at all.
  * Galaxy S (not able to change volume see [issue 254](https://code.google.com/p/csipsimple/issues/detail?id=254))
  * Sony X10 / X10 mini (micro record both mic+line : everything spread through speaker is recorded directly by the micro...)
  * Samsung i5500 (route to rear speaker : [issue 258](https://code.google.com/p/csipsimple/issues/detail?id=258))

Most of the time for this issue, manufacturer is to blame (and maybe also android that doesn't define clearly to manufacturer what should be done).
So be indulgent with android sip applications : solving this kind of issues, is finding a workaround to make things working with a crappy implementation. It can take a lot of time, and having a device to test on is quietly indispensable to be able to really solve this kind of problem... So can take time to solve it.