# qrscanner-test

This is a test project for `cordova-plugin-qrscanner`. It can be used to confirm that the plugin can be built on your development environment.

## Install

Be sure you've followed the Cordova project's instructions for setting up your development environment, then run:

```bash
git clone https://github.com/bitjson/qrscanner-test
cd qrscanner-test
cordova prepare
```

## Run

### Android

```bash
adb devices
# (get the device id from the output)
cordova run android --target= #(device id goes here)
```

### iOS
```bash
cordova run ios
```

### Browser
```bash
cordova run browser
```

## What it should do

When the app loads, the scanner should already be showing, and the first scan should be active. If a QR code is scanned, scanning will stop, and an alert will display the contents. (The video preview will remain active.) Completely close and reload the app to start scanning again.

## How this repo was created

```bash
cordova create qrscanner-test
cd qrscanner-test
cordova platform add android ios browser --save
cordova plugin add cordova-plugin-qrscanner --save

vi www/index.html
# add the following attribute to the body element
#    style="background: none transparent;"

vi www/js/index.js
# add the following at the bottom of the receivedEvent function:
#    window.QRScanner.scan(function(err, contents){
#      err && console.err(err);
#      window.alert(contents);
#    });
#    window.QRScanner.show();

printf 'hooks\nplatforms\nplugins' > .gitignore
```

Now it's possible to follow the instructions from the [Run section](#Run).
