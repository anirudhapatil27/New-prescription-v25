# Dr Patil Digital OPD — V25 Final

This repository packages the approved V25 application as an Android APK.

## Source of truth

- Application source: `DrPatil_Digital_OPD_V25_Final.html`
- V25 is the locked final application model. Do not redesign it or change its clinical workflows, controls, data structures, layout, or font sizes.
- The source includes the restored V8 `printWithMode()` fit-and-print flow and patient-name document title handling for Save as PDF.

## Android build

GitHub Actions builds from a clean runner using Node.js 20, Java 17, Capacitor 6.1.2, and package ID `com.drpatil.digitalopd`.

The workflow creates the Capacitor/Android project from scratch. It does not commit generated Android build output.

## PDF behaviour

- Physical letterhead printing uses Android's native Print Framework.
- Digital letterhead PDF generation uses the locally bundled `html2pdf.js` library and Android FileProvider share sheet.
- The PDF renderer copies and applies V25's existing `@media print` CSS rules without adding replacement font sizes, offsets, or layout coordinates.
- GitHub Actions runs a Chromium PDF-generation smoke test, checks the Android bridge and FileProvider configuration, compiles the APK, checks the package ID, and verifies the APK signature/archive.

## Local data

V25 stores records on the device in local storage. The build preserves the existing data model and backup/import code. Export a V25 backup before replacing an installed app, especially if Android asks you to uninstall the previous build.

## Build

A push to `main` starts the APK workflow. The APK is available under the completed run's Artifacts section.
