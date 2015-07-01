# 1.02 #
  * Android 5.0 support.
  * Option to rewrite inside dialer.
  * Bug fixes.
  * New wizards.

# 1.00 #
  * New AMR-WB codec if available on device
  * Various fixes for android 4.2.
  * Backup/restore integrated to android OS
  * Improvements in TLS and ZRTP features.
  * New wizards.
  * G729 dropped from main app due to its license and now available as separate plugin (or you can build it from source code by your own if use for tests purpose).
  * New codec supported as plugin in codec pack1 : AAC.
  * Bug fixes.
  * Extends possibilities for new plugins to be released.

# 0.04 #
  * Secure SIP transport TLS feature.
  * Secure media transport with SRTP or ZRTP
  * New user interface to match android 4.x guidelines
  * Various new wizards
  * New expert features from pjsip 2.x improvement
  * Codecs list is now :
    * pcmu/a (aka g711u/a);
    * speex
    * g722
    * gsm
    * iSAC
    * SILK
    * G729
    * AMR (depending on device capabilities)
  * And with extra plugin (https://play.google.com/store/apps/details?id=com.csipsimple.plugins.codecs.pack1) :
    * OPUS
    * g726
    * g722.1
    * codec2
  * Bug fixes

# 0.03 #
  * Bug fixes
  * Improve incoming call reliablity
  * Plugins for outgoing call handler
  * AMR-NB codec for device with the library available in ROM
  * WebRTC echo canceller and iLBC codec implementation


# 0.02 #
(current is 0.02-03 : it solves default configuration and the quit feature)
  * Many bug fixes
  * Battery usage improvement
  * Theming of the app by third party app (+ gingerbread theme by default)
  * Multiple calls management (conferencing) - OPTIONAL -
  * Compact mode option to reduce network usage
  * Android 2.3 integration : new micro and audio mode
  * Android 2.3 integration : seamless call intents


# 0.01 #
  * Voice mails
  * SILK codec
  * Improved filter / rewriting rules
  * New wizards
  * Some bug fix and auto configuration
  * Added support for sip: and skype: protocols
  * Codecs priority per bandwidth type
  * Use bundle mode for safe upgrades
  * Add Speex Accoustic Echo canceller
  * Fix problems with gizmo5
  * More devices supported

# 0.00-16 #
  * Call recording feature ! (use menu on In Call screen)
  * Missed call notification
  * Widget to activate/deactivate accounts
  * Add some wizards and refactor all wizard engine
  * Improve audio driver for low cpu devices and 1.6 and under devices.
  * Added soft amplification sliders while in call (stands for volume for devices that doesn't support android audio volume, and is available to all others users if they want to increase in call volume (speaker and mic) more strongly)
  * Improve help / faq
  * Make quit feature easier to understand by mainstream users
  * Start accessibility task force
  * G729
  * Local account => Be aware of what you are doing if you try this one !!! Normally absolutely USELESS on a mobile phone, unless you want to play within your local wifi network...


# 0.00-15 #
  * Disable STUN by default. If you experiment issues with audio please re-enable STUN in media settings.

# 0.00-14 #

  * Fix force close while making a tel: call and csipsimple not started before
  * Samsung Galaxy S (and I9000) fix for speakerphone
  * IPv6 basic support (doesn't support dns resolution but if you set registrar and proxy with ipv6 address should be fine - see [issue 265](https://code.google.com/p/csipsimple/issues/detail?id=265))
  * HTC Evo tweak for the PSP wifi mode bug from HTC (already fixed for N1 & Desire, but default setting to tweak was not set for Evo : see [issue 277](https://code.google.com/p/csipsimple/issues/detail?id=277))
  * Sipgate & PlanetPhone wizard
  * DTMF Info option in settings
  * DNS SRV support
  * Default stun server (thx goes to ekiga guys that are agree to let us use their stun server as default parameter)
  * Armv4 support
  * New translations (thanks goes to translators that spend time on Launchpad to translate the project !! when written : bg, de, fr, hu, it, nl, pt, ru)
  * Bluetooth for 2.2.1


# 0.00-13 #

First beta release