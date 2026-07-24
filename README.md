# AdaModz CityRay / Atlas Clock

Native Android 11 clock studio for Geely head units.

## Identity

- Application ID: `com.Gadamodz.AnalogClock`
- Display name: `AdaModz Clock`
- Minimum Android: 8.0 (API 26)
- Target Android: 14 (API 34)
- No Internet permission
- No advertising, analytics, Firebase or Google services

## Included faces

1. CityRay Horizon
2. Atlas Grand
3. Minimal Night
4. GTS4 Business
5. Concentric Drive
6. Simple Chronograph
7. Oyster Black
8. My Watch Face

## Floating widget

- Full-screen clock: open the app and tap **Hide controls**.
- OneOS floating clock: tap **Show floating**, drag/resize, then tap **LOCK**.
- Exact repositioning: reopen the app and tap **Move / resize**.
- Boot persistence: enable **Start on boot** after granting overlay permission.
- Rounded MusicWidget-style edges in every state.
- Tap a locked clock to fade it to 10% and make it touch-through for 10 seconds.
- **Background: clear** removes dark face backgrounds; **Background: black** restores them.

The tested G426J1 OneOS launcher does not expose standard AppWidget or live-wallpaper pickers. Version 1.3.0 therefore focuses on the same overlay-window model as MusicWidget.

The same selected face and seconds preference are shared by all modes.

The app does not request Internet, location, microphone, accessibility,
notification-listener, or package-scanning access.

## Custom face import

Use **Import face** for:

- PNG, JPG and WebP backgrounds
- Animated GIF backgrounds
- Zepp watch-face ZIP packages
- Layered TBWF packages with their original moving hands
- Zepp palette/TGA images disguised with a `.png` extension

Imported files are copied into private app storage so the wallpaper and screen saver can still load after a reboot or USB removal.

The supplied `UIHH` `.bin` generation is detected but is not treated as a normal image. Its resource table is not decoded reliably by the available parser. Export that face as a PNG/GIF preview, then import the preview.

## HU test

```text
adb install -r AdaModz_AnalogClock_1.3.0_Widget.apk
adb shell am start -n com.Gadamodz.AnalogClock/com.adamodz.cityrayclock.MainActivity
```

If OneOS hides the overlay-permission page, grant only that app-op:

```text
adb shell appops set com.Gadamodz.AnalogClock SYSTEM_ALERT_WINDOW allow
```

The standard Android dream picker can be opened with:

```text
adb shell am start -a android.settings.DREAM_SETTINGS
```

Some Geely OneOS builds hide the dream picker. Full-screen clock mode remains available and does not require privileged vehicle permissions.
