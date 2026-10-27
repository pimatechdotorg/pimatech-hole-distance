# PimaTech Hole Distance Calculator

Native offline Android calculator for center-to-center distance between two separate round holes. Same size is the default; Different sizes enables independent target and measured diameters for Hole 1 and Hole 2.

Version 1.0.1 development preview · Android 8.0+ · MIT license.

## Operation

1. Enter the target center distance.
2. Enter target and measured hole diameters. In Same size mode, one pair applies to both holes. Different sizes opens two pairs. Returning to Same size replaces Hole 2 diameters with Hole 1 values.
3. Select Outside span (far walls) or Inside gap (nearest walls).
4. Enter the span measured along the line joining the hole centers.
5. Read the calculated center distance and signed calculated-minus-target deviation. Positive means centers are farther apart; negative means closer together.

The green C line identifies calculated actual centers. Both Outside and Inside labels show calculated spans at target centers using actual measured diameters. Yellow identifies the selected span type. Tap the diagram to expand it. The drawing is schematic, not a measurement scale.

“Span at target centers” uses the **measured** diameters to tell you what the selected span should be if the centers match the target. Tap the result to also see the nominal span using **target** diameters, equivalent inside/outside spans, and each diameter's deviation.

Switching measurement mode converts a valid span to its equivalent and preserves calculated centers. If the setup is invalid, the existing span remains for correction. Unit changes preserve physical dimensions. Decimal inputs and settings save locally. Reset restores the example while retaining display units.

## Example

- Target centers: 2.000000 in
- Both target diameters: 0.500000 in
- Both measured diameters: 0.501000 in
- Measured outside span: 2.502000 in
- Calculated centers: **2.001000 in**
- Center deviation: **+0.001000 in**, over target
- Outside span at target centers, measured diameters: **2.501000 in**
- Nominal outside span, target diameters: **2.500000 in**
- Equivalent measured inside gap: **1.500000 in**

## Measurement model

Let R = (measured diameter 1 + measured diameter 2) / 2.

- Outside measurement: C = M − R
- Inside measurement: C = M + R
- Deviation = calculated C − target C
- Outside span at target centers = target C + R
- Inside gap at target centers = target C − R
- Nominal span replaces R with the average of the target diameters.

This assumes two separate round holes with parallel axes, measured in the same plane along their centers. It does not determine the direction of positional error or true position relative to datums. It is not a GD&T tolerance assessment.

Use measured hole diameters, not loose pin diameters. Off-center chords, skewed jaws, burrs, chamfers, out-of-round holes, wear and instrument uncertainty affect the measurement. Tangency is allowed (zero inside gap); overlap is rejected. No calibration, temperature or uncertainty corrections are applied. Display resolution does not imply measurement accuracy.

## Installation

Download the APK to Android and open it. Allow installation from that browser/file manager if Android asks. This installs as a separate app, package `com.pimatech.holedistance`; existing PimaTech tools remain installed. This development APK is not a Google Play release and has not undergone a physical-device measurement acceptance test by the developer.

No Internet permission, accounts, advertisements or analytics. App data backup is disabled.

## Build

JDK 17, Android SDK 35 / Build Tools 35.0.0, Gradle 8.9, AGP 8.7.3, Kotlin 2.0.21. Dependencies are pinned to the existing PimaTech calculator family. Set `sdk.dir` in a local, uncommitted `local.properties`, or set `ANDROID_HOME`.

```sh
./gradlew :engine:test :app:assembleDebug :app:lintDebug :app:testDebugUnitTest
```

The output is `app/build/outputs/apk/debug/app-debug.apk`. A local debug key is created by the Android toolchain unless an existing key is supplied with `-PpimatechDebugKeystore=/absolute/private/path/to/key.keystore`. Keep the published preview's private key separately to sign updates; it is intentionally absent from source.

See `docs/ENGINEERING.md` for numerical behavior and `docs/VALIDATION.md` for this build's verified results.

Every app page and dialog displays:

> Proudly made and released open source by PimaTech.org

## Downloads and repository contents

[Android APK](https://github.com/pimatechdotorg/pimatech-hole-distance/releases/download/v1.0.1-preview/Pimatech-Hole-Distance-1.0.1-debug.apk) · [Source archive](https://github.com/pimatechdotorg/pimatech-hole-distance/releases/download/v1.0.1-preview/Pimatech-Hole-Distance-1.0.1-Source.zip) · [Release notes](https://github.com/pimatechdotorg/pimatech-hole-distance/releases/tag/v1.0.1-preview)

The complete multi-module source, Gradle wrapper, documentation, test results and native UI proof images are supplied in `Pimatech-Hole-Distance-1.0.1-Source.zip` at the repository root and as a release asset. Extract that archive to build; the source tree is not expanded in this repository. Private signing keys are excluded.

Owner reviewed version 1.0.1 on Android and approved publication. Developer validation and limitations are documented in the archive.
