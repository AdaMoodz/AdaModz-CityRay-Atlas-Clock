# AdaModz CityRay / Atlas Clock

Native Android 11 clock studio for Geely head units.

## Identity

- Application ID: `com.Gadamodz.AnalogClock`
- Display name: `AdaModz Clock`
- Minimum Android: 8.0 (API 26)
- Target Android: 14 (API 34)
- No Internet permission
- No advertising, analytics, Firebase or Google services

## Included artwork

- 19 high-resolution stock watch faces with face-specific image hands and calibrated pivots.
- 13 transparent Time Frames for decorating the CityRay system clock or an AdaModz face.
- Watch Face and Time Frame are independent layers: either one or both can be enabled.
- Each layer keeps its own X/Y position, width, height, and size preset.
- Each layer has its own background transparency setting.
- Imported face support with a dedicated delete action.

## Floating widget

- OneOS floating clock: tap **Show floating**, drag/resize, then tap **LOCK**.
- Exact repositioning: reopen the app and tap **Move / resize**.
- Boot persistence: enable **Start on boot** after granting overlay permission.
- A fully transparent overlay window: no black backdrop, tint, rounded window, or shadow outside the selected watch-face artwork.
- Tap a locked clock to fade it to 10% and make it touch-through for 10 seconds.
- Both layers appear on the home screen. Only Watch Face may appear inside selected apps;
  Time Frame is always home-screen only.

## Clock Studio UI

- Responsive NeonBlade-inspired control deck with separate cyan Watch Face and magenta Time Frame cards.
- Bottom-anchored translucent control dock keeps the live overlay visible above the settings.
- Native Android neon toggles with explicit ON/OFF labels and large in-car touch targets.
- Static corner-cut styling with no decorative flicker, pulse, scan, or particle animation.

The stock CityRay/OneOS clock is owned by the launcher or System UI. A normal overlay app cannot
reliably hide it; doing so needs a launcher setting, a vendor-signed system app, or root access.
AdaModz deliberately does not present a misleading switch that cannot control it.

The tested G426J1 OneOS launcher does not expose standard AppWidget or live-wallpaper pickers. Version 1.3.0 therefore focuses on the same overlay-window model as MusicWidget.

The app does not request Internet, location, microphone, or notification-listener access.
Its optional accessibility service reads only foreground app/window changes so the overlay can
stay on the launcher and disappear from applications that were not selected.

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
adb install -r AdaModz-CityRay-Clock-v1.10.2-release.apk
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
