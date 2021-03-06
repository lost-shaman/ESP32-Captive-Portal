# ESP32-Captive-Portal
Converts the ESP32 into a captive portal. It uses [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncTCP) library to serve the files and `DNSServer` to redirect all requests. In order for the captive portal to work on some devices, I have to use non local IP address like 172.x.x.x for `WiFi.softAPConfig();`

The captive portal webpage is flashed using this [tool](https://randomnerdtutorials.com/install-esp32-filesystem-uploader-arduino-ide/) but Platformio already included this tool see [this](https://docs.platformio.org/en/latest/platforms/espressif32.html#uploading-files-to-file-system-spiffs). The files are accessed and served using `SPIFFS` via `request->send(SPIFFS, "/index.html", "text/html");`. I kept the flash usage under 1.5MB but yours may vary. I you changed your partition sizes, re-upload the files again.

Once the user accepted the "Sign-in" the user will be redirected to the Captive Portal. The included example plays "Never Gonna Give You Up" if the user clicks the "Click to Start Browsing" button on the portal.
