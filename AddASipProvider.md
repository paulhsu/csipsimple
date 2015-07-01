# Introduction #
In order to provide a better user experience, CSipSimple contains wizards so that users will be able to quickly configure their SIP account with their SIP service.

# Why wizards ? #
  * Have a fancy icon :)
  * Make faster the way to configure the account
  * Be sure than once configured with the account it will work and that the configuration has been validated by SIP provider or users that successfully configured their account with these settings.
  * Sometimes it can also adds some feature such as account balance.

All these reason are not about the SIP provider but about SIP provider's users. Reason why there is absolutely no problem for the free/opensource project that CSipSimple is to add new wizards provided the fact the SIP provider has mainstream users :)

# What should be done before proposing a wizard ? #
You have to make sure that the app can work with your service. So download and install the application and start configuring it. You can use Basic, Advanced or Expert wizard (depending on the need of specific configuration you need to make things work with your service).

You can also play with ExpertSettingMode to activate/deactivate some options to tweak the application for your server. For example, `compact mode` can help to reduce bandwidth if your server does support it; `codec list` can help to have better codec negotiation too. `DNS SRV` and `STUN` option could also be mandatory for your server.

The complete list of available settings is also available in the [developer documentation](http://r3gis3r.github.com/SampleCSipSimpleApp/javadoc/com/csipsimple/api/SipConfigManager.html). But if you have a look on ExpertSettingMode using graphical interface it should be enough.

If you experiment problems, feel free to contact the email : developers _at_ csipsimple _dot_ com. With details on what you usually provide to users to configure standard sip client. If you have other tutorial for other sip client it may also help to find correct adapted settings for csipsimple.

Once this is done and working properly, you can create a new wizard request to add your wizard to the application.

# Information to provide #

  * a 96x96px png icon for the wizard. (if you have the icon on a vectorial format such as SVG it would be even better because it will allow me to generate for all devices screen density).
  * Account settings that should be hard coded for your service. For example, sip registrar, sip proxy or any settings that you find to work better with your service when configuring csipsimple in account expert mode.
  * Eventually properties of remaining fields for user (for example if username is always a phone number, tell me I'll automatically raise the dialpad keyboard instead of the text keyboard which will make faster configuration for the user.
  * Global settings that you would like to automatically activate when an user create an account with your service (for example activate stun or dns srv resolution etc)
  * List of countries where your service is distributed or focused **OR** if it's a service available world wide. It will imply where the account is listed.

You can open a new issue on the tracker of this website with information.

Alternatively you can send all of that to developers _at_ csipsimple.com. (But since I'm sometimes very busy and postpone for a little while, mail could be lost in my stack of mails to treat ;) )

# Next steps #
Once I get these infos, I'll add as soon as possible the wizard in the source code. It will be then automatically built in next nightly build so that you can test that everything goes well on your service and do more advanced tests.

If you opened an issue, the issue will be marked as fixed with the version of the application that will include the wizard. So you will be able to find the minimal version to install from instructions on HowToInstallDevVersion.

If you notice that something is wrong do not hesitate to tell it on the issue so that it can be fixed.

Later, when the development builds will be freezed and then released on the android market, it will contains your wizard.

It's important to do the tests on nightly builds because I never do a build just to add or fix a wizard (users can always fallback on another generic wizard).

# How could we help the application development? #
CSipSimple is an opensource and free software released under GPL license terms. It does not (and will never) do commercial benefit on it.

As you may know there is a lot of android devices and it's sometimes hard to do tests in order to get audio layer working perfect on all devices. -- Many manufacturers do weird things with their audio drivers which requires to find hack on the application --

If you want to help to develop the app and support most devices and more users, and be fancier and with more features, feel free to contribute by [donating](Donate.md) the application.