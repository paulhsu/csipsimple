As security is important stuff on mobile system, Android has a permissions system. It's up to users to be really careful with what permission he grant to an application.

You have no big fear to have with CSipSimple cause it's an opensource application and you can read the code in the Source tab here and ensure that nothing bad is done with your private datas.

But as most users may not have skills to read java and C code, this page is here to explain what permissions are used by CSipSimple and why it use these permissions.


# Permissions used by CSipSimple #

## INTERNET ##
Obviously as SIP application has to communicate with your SIP server it requires permission to access the network.
Be careful if you have a limited 3G data plan and don't want CSipSimple to use your 3G connection to communicate with your server to left "I'm allowed to Use mobile data" deactivated.
CSipSimple may also do some network traffic when you use a wizard with balance inquiry feature (such as ippi and betamax clones). But that's done only when you go in the wizard. It also use network for the FAQ that is hosted on this website.


## RECORD\_AUDIO ##
It's useful to allow remote party to hear you ;)

## MODIFY\_AUDIO\_SETTINGS ##
## WRITE\_SETTINGS ##
It allow CSipSimple to change audio routing. For example routing to earpiece/rear speaker. It also allow CSipSimple to put the phone in silent/vibrate mode while in SIP call if an incoming GSM call arrives. If I do not your hear may explode if there is an incoming GSM call that ring !

## PROCESS\_OUTGOING\_CALLS ##
It allows the application to integrate android when an outgoing call is made. And propose you a popup that allows you to choose between a SIP account and GSM.
If you disable the feature in CSipSimple to "Integrate dialer" it will not process outgoing calls and just leave the standard telephony application manage it.

## READ\_PHONE\_STATE ##
Even if not properly managed yet it will allow the application to be aware about the fact there is an ongoing/incoming GSM call and so do what should be done for your SIP calls.

## ACCESS\_WIFI\_STATE ##
## ACCESS\_NETWORK\_STATE ##
It allows the application to know about the fact you are using wifi / mobile data and so act regarding that (register/do not register, allow you to place sip calls or not).

## RECEIVE\_BOOT\_COMPLETED ##
With this permission the app should be able to automatically start. Don't be afraid, it does not mean that the app will be **running** in background. And by running I mean doing something : many users confuse with an app running and an active process app. Android manage a clever way your phone memory in recent android versions. As consequence an app can be listed by task managers but actually do nothing and so consume no battery. So if CSipSimple is properly configured it should not be hurting to register at autostart. It will auto stop itself (auto stop doesn't mean kill but regarding resources consumptions it is the same).

## READ\_CONTACTS ##
Allow contact integration within the application. Also allow to show contact picture and ringtone when there is an incoming call.

## WRITE\_CONTACTS ##
Allows to update SIP presence information. Also allow to write in your favorites a "csip" uri when you set the information to use for the favorite group as SIP data.

## CALL\_PHONE ##
This is useful for GSM dialer integration. If call is not treat by CSipSimple it forward the request to the GSM dialer.
Also be careful, by default CSipSimple user interface allow you to use mobile calls directly from its user interface. Check the little icon on the top right ;). There is a setting to prevent the use of GSM calls in CSipSimple interface that you can configure in settings.

## CALL\_PRIVILEGED ##
For android 2.3 sip integration and android 4.0 tel integration in case the application is distributed as part of a ROM distribution. It should normally not be granted by android when distributed as third party application and not be used by the application in this case.

## WAKE\_LOCK ##
Allow CSipSimple to acquire wake locks when in call or when setup to do so when registered. Wake lock allows the application to ask CPU to stay active or to ask screen to stay enlighten. It's used only when necessary and is often configurable.

## DISABLE\_KEYGUARD ##
Allow the application to remove keyguard when the phone is in keylock mode. With this permission csipsimple is able to wakeup the phone and disable keyguard while you are in call or received an incoming call. It will reactivate keyguard when call is finished.

## VIBRATE ##
For vibrate ringing mode and for dialer feedback.

## BLUETOOTH ##
For using bluetooth device. There is still known problems to use fully Bluetooth SCO as implementation and what is allowed by manufacturers depends from a device to another.

## READ\_LOGS ##
It is useful for the embedded issue reporting tool. CSipSimple use the standard logging system to write logs. To get back logs and send it to developers, it requires the permission to read logs. It's interesting for us to get the entire logs cause we can get some interesting logs about the audio driver of the phone for example. Or logs from network stack.
If you don't use embedded issue reporting tool this permission will not be used by the application.

## WRITE\_EXTERNAL\_STORAGE ##
Used to write audio records on SDCard, to write backups and logs.

## CAMERA ##
The application is now ready to host the video plugin available for now for alpha testers [here](http://nightlies.csipsimple.com/plugins/CSipSimpleVideoPlugin.apk).
If you don't install the video plugin, this permission will not be used.

## BROADCAST\_STICKY ##
Due to a "bug" in android 4.0 the connection to bluetooth system was requiring this permission (which broke releases 0.03-xx on android 4.0. In order to be compatible with android 4.0 and to be able to connect Bluetooth SCO we need this permission.
If you don't use bluetooth the permission will not be used.

## READ\_PROFILE ##
This permission is only required to be able to get your own photo/picture and display it in the user interface of the SIP Messaging feature. It's never used elsewhere. Besides this feature only works for android > 3.x (was not possible before). So if you are using android before 3.x you'll not see your own photo in the messaging interface.

## WRITE\_CALL\_LOG ##
Introduced in android 4.1 this permission is used to be able to integrate CSipSimple call logs to stock call logs. There is an option in CSipSimple settings to disable call log integration if you don't want the application to use this feature.

## USE\_SIP ##
## CONFIGURE\_SIP ##
This is mostly for internal use. CSipSimple may provide other application to control SIP calls and messages and also SIP configuration. To restrict rights of other apps to do that. There is these two rights.
Besides USE\_SIP is also the permission used by the stock SIP application. As consequence for the future it will allow CSipSimple to use the stock SIP stack in addition to pjsip stack.

# Permissions provided by CSipSimple #

CSipSimple may provide other apps a way to automatically configure your accounts or to override the calls screen or to place SIP calls.
To restrict the numbers of applications allowed to do that, it announce permission that for which other apps should have grants if they wants to use SIP service.
These permissions are :
Use SIP (for make calls and control calls) and Configure SIP for read/write access to your sip datas (account configuration/sip call logs/sip messages...).

So be careful with the apps you grant these permissions.
By allowing an application to use some permission on android you **trust** the application. Do not **trust** anybody ;).