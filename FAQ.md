# Summary #


For non listed question, do not hesitate to join and ask on the users group :

http://groups.google.com/group/csipsimple-users (csipsimple-users@googlegroups.com).


---

# Before starting #
If you don't know what is SIP and what this program does : [WhatIsSIP](WhatIsSIP.md)


---

# The other party can hear me but I can not hear them #
  * It's probably a NAT problem. Some networks are NATed network. It means that there is some network equipment between you and the rest of the world that "hide" your IP address to the rest and the world. It results that your SIP client will not announce properly your IP to sip server and other party. So when a call is placed and media stream is established, the remote party doesn't know where to send its stream and you can't hear him.

To solve this problem, you **must** activate **STUN** :

Go on setting **Settings > Network - Tick "Use Stun"** and fill a stun server on the field bellow.

CSipSimple has a default a stun server **if you activate STUN option !** (but as soon as you do not activate the STUN setting it is not used), if you want to use another STUN server than the default one, you can see http://www.voip-info.org/wiki/view/STUN Public Stun server section to know what server you could use freely.

You can also try to use ICE in addition to STUN if STUN alone doesn't solve the problem :
**Settings > Network - Tick "Use ICE"**


  * Another possible root cause is a problem with Bluetooth feature. Since the app tries to automatically switch to Bluetooth, but that not all devices ROM gives the correct feedback about actual Bluetooth pairing, it may route audio to some virtual device and so you can't talk in the virtual micro :).
In this case, try to disable Bluetooth option of your phone (even if nothing is paired).

  * If it doesn't help, there is maybe a problem with your device (on some device, manufacturers does strange things with the android audio stack). So report the problem on the issue section.

  * It can also be something with codec negotiation. So it can be interesting to try to disable all codecs but PCMU (aka G711u aka uLaw). To do so, go in settings > media > codecs. And long press each other codecs until you get the popup to tell that you want to disable it.


---

# Audio not received/sent #

If you have problem with no audio on one of the side you can start to eliminate some use case before reporting a problem.

  * While in call, you can press the last menu item on the bottom bar that shows a popup with audio activity.

If it's the remote that doesn't ear you, focus on the micro activity :
  1. If you see no activity on the micro bar it's probably a problem with the audio layer of the device. You can try to see the instructions here on Audio troubleshooting. If you report an issue, give your device model and the settings your tried in "audio troubleshooting section".
  1. If you see activity on the micro bar but the remote doesn't here you, the problem is more likely with network. In this case check the STUN settings on the remote side. It's more likely a problem on remote side in this case. (Note : remote side here can be the actual remote sip client or the sip server in the middle if it's a media gateway).

If it's the app that doesn't produce sound, focus on the speaker activity :
  1. If there is activity but you ear nothing, it's probably a problem with the audio layer. Try the Audio troubleshooting instructions and try to change the way the app renders sound (earpiece, speaker, bluetooth, headset). If you report an issue, give your device model, settings you tried in "audio troubleshooting section" and the audio device (earpiece, speaker, bluetooth, headset).
  1. If there is no activity here, it's probably because the app doesn't announce a suitable way to reach it in network negotiation. Please have a look to the instructions about about STUN. It might also be something with codec negotiation. You can try to disable all codecs but one you know to be supported by remote side (Note : remote side here can be the actual remote sip client or the sip server in the middle if it's a media gateway).


---

# Call stops after 30 seconds #

This is probably a configuration problem. You should ask your sip provider for settings they expect (particularly whether they expect to be the sip proxy or have a different sip proxy address).

If the call cuts automatically after 30seconds it's because the app never received the confirmation of the fact the call is established. In such situation sip protocol indicates that the call is not valid anymore.



---

# There is no contact list #

Just try to make a call using the standard android phone dialer, or clicking a contact in the official contact application ;).... And you'll see that a contact list is not needed at all in the SIP application !!!
There is also a quick text search dialer if you switch to text dialing mode, that will search on android contacts.


---


# When integrated to android, I don't want some number to be handled by SIP #
## I want to automatically add prefix/rewrite some numbers ##
There is a powerful rewriting/filter/auto-answer tool in CSipSimple (see the UsingFilters wiki page).
To access this tool, go on the account on which you want to apply things. Press menu button and choose "Filters".
You are now in the tool. Using this tool you can :
  * Rewrite numbers : for example add prefix, suffix, completely replace the number by another one, or apply a custom regexp - if you don't know what a regexp is, don't use it ;).
  * Don't call some numbers : if you don't want some number to be managed by this account, for example call to other mobiles phone etc, you can add an exclude rule. Then when you'll dial **from native dialer/contact app** if the phone number match this rule, this sip account will not be proposed in the list of choices you have and if there is no SIP account that can handle this number, it will automatically use Mobile without asking you anything
  * Force call some numbers using this account : same thing that the last point, but here it will not exclude, but force the call to use this account and will not ask you for anything.
  * Auto answer : if you want to automatically answer to some phone number, you can add a rule here. It's useful if you are using some call callback feature from your provider.


---

# Is there a way to close the application? #
Yes, but you have to configure CSipSimple according to the fact you want to be able to close it !

Let me explain : CSipSimple can run under several setting configuration :
  * "Always available" when you want to be able to receive calls
  * "Only for outgoing calls" when you only want to use sip for outgoing calls (CSipSimple starts when you dial from native dialer or when you launch the application).

When you set "Always available", close option make no sense : indeed, the application will automatically restart when network will change of state... and you'll say me "Hey there's a bug... the app constantly restart itself". By using this profile you tell the software that you want to receive your calls, and it will do it's best to be running when you can receive calls.

However, if you choose "Only for outgoing"... Close option will appear in the menu of CSipSimple dialer! Since here, it make sense to use this option, since the app will never restart itself.


---

# On 3G I don't always receive calls #
  * Your carrier network probably cut the UDP connection so that you can't receive calls anymore. To keep your connection alive you have to setup CSipSimple to be more aggressive.
To do so, transform your account into an Expert account (Edit account, press menu, "Choose wizard" and choose Expert). Edit again the account, there is now more settings to set. Try this :

  * Re-Register (register timeout) : 184
  * Keep Alive : 100

  * According your device, you may also try to activate CPU lock.
Switch to ExpertSettingMode and in User interface settings activate "Use partial wake lock".


---

# I receive calls twice / Registration is done on the sip server twice #

You SIP server probably don't support fully the RFC and the registration method used by CSipSimple by default is not suitable for your server. Fortunately, there is a way to configure your account to avoid that :

To do so, transform your account into an Expert account (Edit account, press menu, "Choose wizard" and choose Expert). Edit again the account, there is now more settings to set. Try this :

  * Contact rewrite method : legacy
  * (or if it doesn't work try to disable "Allow contact rewrite")

If your server actually doesn't support the latest RFC you may have to wait for about 15 min for the current registration to timeout.

In order to improve CSipSimple, if you are experimenting this issue and that this workaround help, you can inform us about that and tell us what is your SIP provider so that we could add a wizard with this enabled by default.

You can also notify your SIP provider that they are not fully RFC compliant (their server doesn't respect the normalization : and precising them that they do not respect RFC 3261 about contact rewrite method)


---

# I can't end calls #

It's possible that your SIP server doesn't support actually TCP (in terms of SIP RFC compliance). Fortunately, there is a way to configure your account to force the use of UDP only :

To do so, transform your account into an Expert account (Edit account, press menu, "Choose wizard" and choose Expert). Edit again the account, there is now more settings to set. Try this :

  * Transport : choose UDP is the list of transport.

In order to improve CSipSimple, if you are experimenting this issue and that this workaround help, you can inform us about that and tell us what is your SIP provider so that we could add a wizard with this enabled by default.


---

# Audio routing troubleshooting #
If you are experimenting audio automatically routed through rear speaker instead of earpiece or other problem with audio driver on your phone, it's probably cause manufacturer implement a strange way its audio driver and android official API for routing audio.

Fortunately, there is some common behavior that can be managed by activating some "hacks" in CSipSimple.

To do so :
  1. Install a dev version (HowToInstallDevVersion wiki page).
  1. Switch to ExpertSettingMode (wiki page) global setting section.
  1. Try to play with these settings (available in Media settings > ... (bottom of the list):
    * Use Mode API (try to use this one first and without activating others)
    * Use Routing API.
    * Use tone hack.
    * Use WebRTC implementation
    * Change the micro source (if related to the way micro records - big echo for example)
    * Change Audio Mode for SIP calls

Try each of these settings independently and then in combination.

If one or a combination of that modes helps... well good news for you, you have CSipSimple running correctly on your phone ;).
You can then share with me which setting helps so that I can automatically turn on one of the correct hack by default for your device.

To do so, I need the exact device info (the infos announced by android to the application about the device). An easy way to collect these info is to send me logs using my embedded tool : see HowToCollectLogs.

If it doesn't work you can install other apps on the market such as "Device Info" and tell me what are the "Device" and "Product" values.

It's possible that none of these settings helps (for example it's currently a known issue on samsung moment). In this case we have to cross finger for your manufacturer or a custom ROM maker to fix that in the ROM directly. Maybe another hack could be found for your device too, but it requires devs skills and a phone to test on. If you are in this case, you can contact us so that we can give you what to test on source code to troubleshoot the problem.


---

# When screen goes off sound quality is bad #

That's cause of the fact your device has special policy when screen goes off.
There are a few well known reasons for it:
  * Could be cause of the PSP behavior of the wifi card (see http://code.google.com/p/android/issues/detail?id=9781)
  * Could be due to the fact you have setCPU that change CPU speed when screen goes off.
  * Sometimes "Wi-Fi optimization" in the advanced settings for your Wi-Fi connection can cause packet loss and latency. Try disabling the setting and see if your connection improves.

Fortunately, there is an existing workaround in CSipSimple to prevent screen going off and so keeping up the good call quality.
To activate this workaround if not automatically detected by CSipSimple (there is an autodetection done for the PSP behavior).

  1. Switch to ExpertSettingMode (wiki page) global setting section.
  1. In User interface section scroll to "Keep awake while in call" option and activate it

---

# In gingerbread with dialer integration I can't place GSM call anymore #

Actually you can, you just don't know how :).

The first prompt you get is there cause both **CSipSimple** and the **stock SIP** application can intercept the outgoing call to treat it.

If you choose "Dialer", you actually choose the **stock SIP** application !! If you choose CSipSimple, you choose the standard process of telephony intent.

So just choose CSipSimple ! You'll see, next you'll have the CSipSimple chooser which allow to choose Mobile call.

If you don't want to be bothered anymore with the stock chooser that propose you between the stock 2.3 SIP application and CSipSimple, in the first popup _(which CSipSimple don't and CAN'T manage)_, there is checkbox to **remember your choice**.

Activate it and choose CSipSimple. Then you'll not be bothered anymore with this chooser and benefit all powerful features of CSipSimple in terms of Filters and Rewriting rules.


_In future release this will not be relevant anymore. You can try nightly builds if you are hurry to get something working well on gingerbread (there is also cool features for gingerbread included in latests nightlies)_

---


# I did a mistake when I set up the voice mail number, how can I modify it? #
  * First of all, if you have to set up manually the voice mail number of your sip provider it means that the corresponding wizard for this sip provider has not yet the voice mail number automatically configured, so you should ask for that.
  * If this is a non mainstream users provider or if you want to workaround quickly there is an easy solution :
    1. Go in accounts list
    1. Long press on the concerned account
    1. Choose wizard > Expert
    1. Click on the account row
    1. Scroll down to "Voice mail number", change it, and save
    1. Optionally you can revert to the previous wizard by reproducing point 1 to 3.

---


# I try to use ZRTP + SRTP, but ZRTP doesn't work #
That's a known limitation. Due to the fact ZRTP is considered as a plugin for pjsip that already manages SRTP it's own way, you should never try to enable SRTP and ZRTP at the same time.

In fact if you do so, pjsip will ignore ZRTP and use SRTP as media adapter.

It's recommanded to use ZRTP that includes features of SRTP if the remote side is known to also support ZRTP. If your remote side is a sip server that only use SRTP and announce it with SIP mechanism, you'll hove to choose SRTP however.

---


# Cryptography notice #
> This distribution includes cryptographic software. The country in which you currently reside may have restrictions on the import, possession, use, and/or re-export to another country, of encryption software. BEFORE using any encryption software, please check your country's laws, regulations and policies concerning the import, possession, or use, and re-export of encryption software, to see if this is permitted. See <http://www.wassenaar.org/> for more information.

> The U.S. Government Department of Commerce, Bureau of Industry and Security (BIS), has classified this software as Export Commodity Control Number (ECCN) 5D002.C.1, which includes information security software using or performing cryptographic functions with asymmetric algorithms. The form and manner of this CSipSimple distribution makes it eligible for export under the License Exception ENC Technology Software Unrestricted (TSU) exception (see the BIS Export Administration Regulations, Section 740.13) for both object code and source code.