# Introduction #

pjsip allows to add "modules" that extends pjsip features.
As CSipSimple uses pjsip as backend it can benefit of existing modules already developed for pjsip.

However due to the current build toolchain, it's not obvious to integrate with CSipSimple.

This page should help to clarify how to do the best way.

# Reference module #

CSipSimple already include one sample that you can get inspiration from : **[pjsip\_mod\_reghandler](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple#CSipSimple%2Fjni%2Fpjsip_mod_reghandler)**

# Folder structure #

You should place your files in a new folder of _CSipSimple/jni_.
The folder structure of your module should be the following :
  * jni
    * ...
    * pjsip\_mod\_your\_module
      * android\_toolchain
        * Android.mk
      * src
        * your source files
      * include
        * your include files
        * a .i file to define swig interface
    * ...


# Integration to toolchain #

The first step is to have your native files built into the dynamic lib loaded by csipsimple so that it can be resolved later when loading it in java space.

To do that, you first need to have c/c++ files built. This is done using the android\_toolchain/Android.mk file.

If you are familiar with android ndk this should be easy. It's about creating a static lib.

You can get inspired of [Android.mk](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/jni/pjsip_mod_reghandler/android_toolchain/Android.mk) if you are not familiar with NDK. Don't forget to name your module (in next steps I'll call your module pjsip\_mod\_your\_module)

Once this file is ok, you need to integrate it with existing files.
So, edit the [main Android.mk](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/jni/Android.mk) to list your new mk file.

Then edit the dynamic lib of [pjsipjni Android.mk](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/jni/csipsimple-wrapper/android_toolchain/Android.mk#60) and add your lib as needed static lib by adding
```
LOCAL_STATIC_LIBRARIES += pjsip_mod_your_module
```

At this point you can try a build to check your c/c++ files are correctly built.

# Integration with jni swig auto bindings #
CSipSimple takes advantage of swig tool to automatically generate java api based on C/C++ api.

You can use the same or do your own bindings based on standard jni if you are familiar with it. Next steps explains how to use swig with your stuff.

  * make your .h files compatible with swig integration.
You can see [here an example](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/jni/pjsip_mod_reghandler/include/pjsip_mobile_reg_handler.h) (with a callback object too).
  * create a .i file to define swig interface.
You can see [here an example](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/jni/pjsip_mod_reghandler/include/mod_reghandler.i) (with a callback object too).
  * integrate your .i and .h to [swig makefile](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/jni/swig-glue/android_toolchain/Android.mk). It's basically to :
    * Create your path shortcut `MOD_YOUR_MOD_ROOT_DIR := $(SWIG_GLUE_PATH)/../pjsip_mod_your_module`
    * Add your .h files to swig headers : `PJ_SWIG_HEADERS += ...`.
    * Add your interface file (.i) to `INTERFACES_FILES`.
    * Add your includes folder to swig generation includes in `$(SWIG) ... -I$(MOD_YOUR_MOD_ROOT_DIR)/include ...`.
    * Add your includes folder to native lib generation : `LOCAL_C_INCLUDES += $(MOD_YOUR_MOD_ROOT_DIR)/include`

At this point you can now launch a `make` build. Now the static lib should be built and the auto jni bindings done.

# Integration in java space #

You have now to implement a PjsipModule interface. See how it's done in [mod\_reghandler](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple#CSipSimple%2Fsrc%2Fcom%2Fcsipsimple%2Fpjsip%2Freghandler).
You have here just to implement the methods. Typically here you will add your module to pjsip endpoint here.

The files here can be in a package of your own project and it's advised to not pollute csipsimple folders here and rather create your own folder.

You can call any native method in your project. You can also get callback from your own callbacks here too.

And the little bit ugly addition.
[here](http://code.google.com/p/csipsimple/source/browse/trunk/CSipSimple/src/com/csipsimple/pjsip/PjSipService.java#2188) in initModules() method you have to add your module you created in previous step just like it's done for the reghandler module. This might change in the future to make it more flexible.