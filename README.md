Android Color Picker
aka AmbilWarna library ("Pick a Color" in Indonesian)
====================

This is a small library for your application to enable the users to select an arbitrary color. 
For example, your application has a feature to customize the color of some background, text, or maybe for a painting application where the user should be able to select different color for painting or filling.

![nexus_4_01](http://img801.imageshack.us/img801/6816/hyn4.png?raw=true) ![nexus_4_02](http://img11.imageshack.us/img11/9462/y805.png?raw=true)

![nexus_4_01](http://img594.imageshack.us/img594/7613/bv48.png?raw=true)

This is a fork of android-color-picker library by brk3 (https://github.com/brk3/android-color-picker).
Comparing to the original project this one targets API level 18 and its min supported SDK level is set to 4. 
The differences also include:

- AlertDialog has been replaced with DialogFragment from Android support library v4
- DialogFragment recreates on configuration change and color is
retrieved from saved state
- Software layer is set programmatically on Android 3+ in AmbilWarnaKotak due to color
blending issue
- Adjusted AmbilWarna DialogFragment for bigger screens
- On Android 3+ user can now set Theme_Holo_Dialog or
Theme_Holo_Light_Dialog on AmbilWarna DialogFragment

This is an Android Library Project which you can include into your main project.

How to use:

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

See ![Wiki](android-color-picker/wiki) for more information.
