Step 1: Install Arduino IDE

Download from official site:
=> https://www.arduino.cc/en/software

Tools → Port(Windows) → COMx 

Tools → Port(Mac) → /dev/cu.usbmodem  

Step 2: Install ESP32 Board Support

1. Open Arduino IDE → File → Preferences
2. Add this URL to "Additional Board Manager URLs":
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

3. Go to Tools → Board → Boards Manager
4. Search for "esp32" and install "esp32 by Espressif Systems" 


Verify Installation

Tools → Board → ESP32 Arduino → ESP32S3 Dev Module
Tools → Port → USB / COM

Arduino IDE Settings (Important)

If using USB-TO-UART

1. Tools → USB CDC On Boot → Disabled

2. Tools → Upload Mode → UART0 / UART

If using USB-OTG

1. Tools → USB CDC On Boot → Enabled
2. Tools → Upload Mode → USB-OTG
3. Tools → USB Mode → CDC and JTAG


Inshort verify Setting if using ESP32 S3====

CASE 1: USING USB-TO-UART (RECOMMENDED / BEGINNER)


Board                : ESP32S3 Dev Module

Port                 : COMx / /dev/cu.usbserial

Upload Speed         : 921600 (or 460800 if error)

CPU Frequency        : 240MHz (WiFi)

Flash Frequency      : 80MHz

Flash Mode           : QIO

Flash Size           : 16MB (or your board size)

Partition Scheme     : Default 4MB with SPIFFS

PSRAM                : Enabled

Arduino Runs On      : Core 1

Events Run On        : Core 1

USB CDC On Boot      : Disabled

Upload Mode          : UART0 / UART

USB Mode             : Disabled

JTAG Adapter         : Disabled


# Serial Monitor Settings

Baud Rate : 115200


Line Ending : Both NL & CR


Upload Speed  : 921600 (or 460800 if error)  

Example : 

void setup() {
  Serial.begin(115200);
}

void loop() {
  Serial.println("ESP32-S3 UART OK");
  delay(1000);
}





CASE 2: USING USB-OTG (NATIVE USB – ADVANCED)

Board                : ESP32S3 Dev Module

Port                 : USB CDC

Upload Speed         : N/A (ignored)

CPU Frequency        : 240MHz (WiFi)

Flash Frequency      : 80MHz

Flash Mode           : QIO

Flash Size           : 16MB

Partition Scheme     : Default

PSRAM                : Enabled

Arduino Runs On      : Core 1

Events Run On        : Core 1

USB CDC On Boot      : Enabled

Upload Mode          : USB-OTG

USB Mode             : CDC and JTAG

JTAG Adapter         : Integrated USB JTAG




# Serial Monitor Settings

Baud Rate : 115200
Line Ending : Both NL & CR

Example : 


void setup() {
  Serial.begin(115200);
  while(!Serial);   // REQUIRED for USB-OTG
}

void loop() {
  Serial.println("ESP32-S3 USB OTG OK");
  delay(1000);
}

