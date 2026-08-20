# Asphalt Bridge V2

A lightweight Android BLE bridge. Android Studio is NOT required on your PC.

## What V2 does

- Scans for likely Fire-Boltt / Asphalt / Da Fit devices.
- Displays all matching devices with RSSI and address.
- Lets you choose the watch.
- Connects over BLE.
- Enumerates GATT services and characteristics.
- Reads readable characteristics.
- Enables notifications/indications where possible.
- Displays raw notification/read packets.
- Sends raw packets to the Windows Python server over Wi-Fi.
- GitHub Actions builds a debug APK automatically.

## Build without Android Studio

1. Create a private GitHub repository named `AsphaltBridge`.
2. Upload the contents of this project.
3. Commit to `main`.
4. Open the repository's `Actions` tab.
5. Select `Build Asphalt Bridge APK`.
6. Run the workflow.
7. When it finishes, open the workflow run.
8. Download the `AsphaltBridge-debug` artifact.
9. Extract it and install `app-debug.apk` on your Android phone.

The PC does not need Android Studio.

## PC Python server

Use the separate Python server package supplied with this project:

    AsphaltBridge_Lite_Python_Server.zip

Start:

    start_server.bat

Find PC Wi-Fi IP:

    ipconfig

Example:

    192.168.1.100

In the Android app enter:

    http://192.168.1.100:8000

The PC and phone must be on the same local network.

## Important

This is intentionally a protocol-discovery build. It does not pretend to know the Asphalt's proprietary sensor packet format.

After connecting, the Python server saves:

    asphalt_packets.jsonl

Send that file back for the next stage. We can then decode the actual packets for HR, SpO2, steps, battery, sleep, etc.

The Bluetooth calling microphone is separate from BLE/GATT on many watches, so it is a later stage.
