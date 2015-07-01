# Introduction #

The project is globally compounded of 3 main parts :
  * CSipSimple which is the Java application for Android
  * pjsip\_android/jni which is the android portage of pjsip for Android
  * pjsip which is checked out at [build](HowToBuild.md) time.

There is also additional parts to bring other features such as codec or encryption.

# Different parts of the projects and license that applies #
## CSipSimple ##

This part of the application is released under a GPLv3 license. There is **no** commercial license for this part of the project.

If you own a commercial license of pjsip library you may also want to use the dual LGPLv3 license allowed by CSipSimple. But keep in mind that you **MUST** have a pjsip license to use this license method.


So conditions of the GPLv3 (or LGPLv3) applies, specially the fact that any redistribution of the application (or library) must also grant GPLv3 (LGPLv3) rights to users (included publishing the code).

The final application **MUST** also redistribute the license (even in LGPL mode) with the full copyright and this must be available from within the application. You also have to notice about that in the description

The application also may to allow third party application to work with CSipSimple (or any redistribution of CSipSimple under GPLv3), we grant the right to any third party application (under any license) to use the API defined within CSipSimple.

This API allow a third party application to rely on CSipSimple (or a redistributed version of CSipSimple under GPLv3), as if it was a SIP service available on the android OS. This API already allow to do many things and can be enriched if any needs appear.

## pjsip\_android/jni ##

This part of the application is released under Apache v2.0 license. It only applies to source code in the jni folder of this project ( CSipSimple/jni -- and only this folder !!! ) when the dependencies are not checked out.

This part will download dependencies that are not covered by this license. See pjsip and other optional parts sections.

## pjsip ##
This part of the application is released under GPLv2 and contains some other third party software.

To get more info about this part of the software please see the [website of the pjsip project](http://www.pjsip.org/licensing.htm). pjsip license owner may arrange an alternative license if you do not comply with this GPL license.

However obtaining a license for this part of the software doesn't grant you the right on the rest of the project (CSipSimple).

## Other optional parts ##
### Codec G729 ###
The source code of this codec glue with pjsip is covered by the GNU-GPLv3 license whom copyright holder of this part is Samuel Vinson (from siphon project). See source code of this part to contact Samuel directly if you need more info about his copyright.

Also, the usage of the codec is not free. Make sure you bought the usage license before activating the codec in CSipSimple. [Synapse Global](http://www.synapseglobal.com/g729_codec_license.html).

### Codec G726 ###

The source code of this codec glue with pjsip is covered by the GNU-GPLv3 license whom copyright holder of this part is Keystream AB. See the source code of this part to contact them.

### ZRTP ###
The source code of this codec glue with pjsip is covered by the GNU-GPLv3 license whom copyright holder of this part is Werner Dittmann. See source code of this part to contact Werner directly if you need more info about his copyright.

### Openssl ###
If you decide to enable TLS or ZRTP, you'll also need to have openssl. The openssl license applies. It mainly means that you have to notice about the fact you use openssl. But read the license to know what can be done.

### Ffmpeg ###
If you decide to use video with ffmpeg codec, you may also have to take care of licenses that applies to your ffmpeg build.


# Rebrand the application for your needs #

## Without any pjsip commercial license and don't plan to get one ##
In this case two solutions :
  * Redistribute a GPLv3 version of the application.
    * _Limitation_ is that you **must** redistribute source code and notice user about the fact it's GPL application on android market and inside the application. All your source code (or patch you apply) must be available to your users. If it's a simple patch you can ask to contribute the core project.
    * _Your app license_ : GPLv3 or compliant
  * You can rely on CSipSimple or any redistribution of it you may do under GPL license terms (call that voip plugin if you want). Then use CSipSimple api folder to be able to use the application as a service available on the phone.
    * _Limitation_ of this case is that you **must** release two applications on the market. The plugin can be proposed by your main application as an application to download to allow user to use voip.
    * _Your app license_ : one (the plugin) must be GPLv3 compliant, and the other under your license.

## With a pjsip commercial license ##
Please contact Teluu about that (see the [website of the pjsip project](http://www.pjsip.org/licensing.htm)).
Once they allowed you to reuse their lib on android. You have now two new solutions :
  * Use only the jni glue released under Apache license terms. This part of source code covers development made specifically for the android portage of pjsip. It contains a glue to present a jni interface your java application. You still have to take care about license of other optional parts of the native library (see section above).
    * _Limitation_ of this case is that you will not benefit of all cool stuff and community support and update of the android specific java part. It will be specially annoying if you want to support most devices since supporting manufacturer audio stack routing is not always easy to do. You'll also lost the filtering rules, account management and other cool features of CSipSimple. And it's not allowed to reuse parts of csipsimple in your code if you choose this way.
    * _Your app license_ : your license if does not break Apache license (should be fine ;) ).
  * Use CSipSimple the LGPLv3 license mode allowed by CSipSimple part. In this case, you will have to respect LGPLv3 license terms. In this case you will reuse the application as an **android library** (see [android library doc](http://developer.android.com/guide/developing/projects/projects-eclipse.html#ReferencingLibraryProject))
    * _Limitation_ is that you **must** contribute any change you do to the library part. You also have ot take care about license of other optional parts of the native library (see section about) if you decide to use these modules.
    * _Your app license_ : your license if does not break the terms of what can do an "Application" in LGPLv3 license terms. It's mainly about the fact that it must include a notice (inside the app and on the distribution channel you use) about the fact it contains CSipSimple as an LGPLv3 library.

## [Known redistributions of CSipSimple](BrandedVersionsOfCSipSimple.md) ##

If you do some rebranding of the application or reuse part in respect with above rules, it is highly appreciated that :
  * You inform us about the fact you rebrand the application or reuse it as library
  * You contribute some [donation](Donate.md) to the project

If you are looking for some freelance to develop your own app based on csipsimple in respect with the above rules, you should drop a mail on the developer google group of CSipSimple project and see if someone is available.

For now main contributors of project do not do rebranding work for companies, but try to help people that are on such a project (depending on time available).