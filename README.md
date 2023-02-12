## Build

This particular README is written with CalyxOS in mind. NOT TESTED! I've added `LOCAL_PRODUCT_MODULE := true` to AndroidAuto's `Android.mk` file. After pulling down the code from Calyx's repo as documented on their site, the stub folder should be placed into `calyxos/android13/prebuilts/`. 

Next, add the following line in `calyxos/android13/vendor/calyx/config/common.mk`:
```
PRODUCT_PACKAGES += AndroidAuto
```
Also, make sure to add Android Auto package name `com.google.android.projection.gearhead` to the role `config_systemAutomotiveProjection` in the line 2150 inside `calyxos/android13/frameworks/base/core/res/res/values/config.xml` file. 

Should look like this: 

```
<!-- The names of the packages that will hold the automotive projection role. -->
<string name="config_systemAutomotiveProjection" translatable="false">com.google.android.projection.gearhead</string>
```

## Verify Build

After going through Calyx's build and sign process, you can check that Android Auto is a privapp. You can do this by going to the file generated in `$OUT/obj/PACKAGING/target_files_intermediates/*.zip`. Within the archive, you can see the folders. Under `/PRODUCT/priv-app/`, you can check that the AndroidAuto folder is present. If it is not, something went wrong with it being added to the build. 

## Post-Flash Setup

- Install the latest Android Auto APK as well as the latest APK for: Google, Google Speech services and Google Maps. As far as I can tell, it doesn't matter if it comes from Aurora Store or if it's from a standalone APK. 

- Open up Google Maps and grant it the location permission. You do not need to be signed in for this.

- Plug your phone into your car. You may or may not have to manually start the pairing process in the car's menu. I had to do this on my 2018 Chevy Volt, but this may depend on your car/head unit's make/model/year.

- When firing it up and doing the initial setup, it may say Maps needs locations permissions. If it's set, you can cancel out of that and it should accept it.

- Android Auto should simply work now.

## Thanks
- Thank you to @dylangerdaly for starting the initial effort.
- Thank you to @SolidHal for the continuation of this effort and writing the code this repo was forked from.
- Thank you to @JQuilty for the latest android 12L patches.
- Thanks to everyone in this thread that's contributed and tested - https://github.com/microg/GmsCore/issues/897
- Thanks to the MicroG developers.
- Thanks to the CalyxOS developers.
- Thanks to @chirayudesai in particular for all the help in the CalyxOS Matrix server.
