# Wi-Fi Signal Mapper (Option C)

Android Studio project (Kotlin, XML layout). Reads Wi-Fi RSSI with `WifiManager` / `WifiInfo.getRssi()`,
shows it live every second, and saves 10 labelled readings per press of **Record** to `readings.csv`.

## Open and run
1. Android Studio -> File -> Open -> select the `WifiSignalMapper` folder. Let Gradle sync
   (accept any "update plugin / Gradle" suggestion if offered).
2. Phone: Settings -> About phone -> tap Build number 7 times -> Developer options -> enable USB debugging.
3. Connect the phone by USB, choose it in the device drop-down, press Run.
4. Allow the **location** permission (Android requires it to read Wi-Fi info).
5. The phone must be connected to the router's Wi-Fi. The emulator cannot measure real Wi-Fi.

## Measuring
1. Type the distance (m), tick **Wall** if a wall is in between, set the session number (1, 2, 3).
   Label is optional (auto: "5 m, no wall").
2. Stand still, hold the phone the same way, press **Record 10 readings** and wait ~10 s.
3. Repeat for each spot (1, 3, 5, 10, 15 m; then 3, 5, 10 m with wall) in 3 sessions on different times of day.
4. **Share CSV file** sends `readings.csv` to e-mail/Drive. Or in Android Studio:
   View -> Tool Windows -> Device Explorer -> sdcard/Android/data/com.example.wifisignal/files/readings.csv
5. In Excel/Sheets: average RSSI per label and session, then make the chart (no wall vs wall).

CSV columns: timestamp, session, label, distance_m, wall, band, freq_mhz, link_mbps, reading_no, rssi_dbm

## Notes
- Only RSSI, frequency and link speed are saved. SSID/BSSID are not read (privacy rule).
- `connectionInfo` is deprecated on Android 12+ but still returns RSSI for the connected network.
- Newer Android versions may throttle Wi-Fi updates, so consecutive readings can repeat.
- Assignment rule: mark in `MainActivity.kt` which parts were AI-generated, and fill Appendix C.
