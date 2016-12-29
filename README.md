New Android Color Picker
====================

This is a small library for your application to enable the users to select an arbitrary color. 
For example, your application has a feature to customize the color of some background, text, or maybe for a painting application where the user should be able to select different color for painting or filling.

![Nexus 5 screenshot 1](http://i1155.photobucket.com/albums/p549/Antonina_Tkachuk/color_picker_nexus_5_01_zps0eug3cox.png)
![Nexus 5 screenshot 2](http://i1155.photobucket.com/albums/p549/Antonina_Tkachuk/color_picker_nexus_5_02_zpso6vs2y2r.png)

This is a fork of **android-color-picker** library by **brk3** (https://github.com/brk3/android-color-picker).
Comparing to the original project this one is Gradle-based library module which targets **API level 23** and its **min supported API level** is set to **7**. It also has a support library v7 as a dependency.

The differences also include:

- **AlertDialog** has been replaced with **DialogFragment** from **Android support library v7**
- **DialogFragment** recreates on configuration change and color is
retrieved from saved state
- Software layer is set programmatically on **Android 3+** in **AmbilWarnaKotak** due to color
blending issue
- Adjusted **AmbilWarna DialogFragment** for bigger screens
- By default, a compatible theme **Theme.AppCompat.Light.Dialog.Alert** is used. You can always override it for your own customization

This is an **Android Library Module** which you can include into your application project (File > New > Import Module), and whenever used in code - Add module as a dependency.

###How to use

        // create OnAmbilWarnaListener instance
        // new color can be retrieved in onOk() event
        OnAmbilWarnaListener onAmbilWarnaListener = new OnAmbilWarnaListener() {
            @Override
            public void onCancel(AmbilWarnaDialogFragment dialogFragment) {
                Log.d("TAG", "onCancel()");
            }

            @Override
            public void onOk(AmbilWarnaDialogFragment dialogFragment, int color) {
                Log.d("TAG", "onOk(). Color: " + color);

                MainActivity.this.mColor = color;
            }
        };

        // create new instance of AmbilWarnaDialogFragment and set OnAmbilWarnaListener listener to it
        // show dialog fragment with some tag value
        FragmentTransaction ft = getSupportFragmentManager().beginTransaction();
        AmbilWarnaDialogFragment fragment = AmbilWarnaDialogFragment.newInstance(mColor);
        fragment.setOnAmbilWarnaListener(onAmbilWarnaListener);

        fragment.show(ft, "color_picker_dialog");

###See [Wiki](https://github.com/lomza/android-color-picker/wiki) for more details.

## Donate

:yum:

If you want to make me happy - [just drop a few...](https://www.paypal.me/toniatkachuk) ;)
