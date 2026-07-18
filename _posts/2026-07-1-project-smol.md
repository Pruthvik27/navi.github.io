---
layout: post
title: "IoT Telemetry Hub: Building the Node"
---

# IoT Telemetry Hub: The First Prototype
*Date: July 19, 2026*

This project outlines the development of an ESP32-based telemetry hub designed to collect sensor data and transmit it over MQTT. 

## The Hardware Stack
To make this work, I needed components that were cheap, reliable, and capable of operating on 3.3V logic:
* **Microcontroller:** ESP32-WROOM-32
* **Sensors:** BME280 (Temp/Humidity) and INA219 (Voltage/Current)
* **Power:** 18650 Li-ion cell with a TP4056 charging module.

## The Short Circuit Incident
While measuring the dimensions of the 18650 battery holder with my metal calipers, I accidentally bridged the positive and negative terminals. 

![Sparks flying from calipers](/assets/images/image_41379e.jpg)

*Lesson learned: Always use plastic calipers or cover the metal tips with Kapton tape when measuring live batteries!*

## The Code (Snippet)
Here is a quick look at the C++ code used to connect the ESP32 to the WiFi network:

```cpp
#include <WiFi.h>

const char* ssid = "YOUR_SSID";
const char* password = "YOUR_PASSWORD";

void setup() {
  Serial.begin(115200);
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("Connected to WiFi!");
}
