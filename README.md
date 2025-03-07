

# **🌡️ Arduino Temperature & Humidity Monitor with Buzzer Alert 🚨**  

![Arduino](https://img.shields.io/badge/Arduino-Project-blue?style=for-the-badge&logo=arduino)  

### **📌 Overview**  
This project **monitors temperature and humidity** using a **DHT22 sensor** and triggers a **buzzer alarm if the temperature exceeds 40°C**. The data is displayed on the **Serial Monitor**, making it useful for applications like:  

✅ **Greenhouses & Smart Farming**  
✅ **Home & Industrial Temperature Monitoring**  
✅ **Overheat Alerts for Electronics & Machines**  

---

## **🛠 Components Required**  

| **Component** | **Quantity** |
|--------------|-------------|
| Arduino Uno  | 1 |
| DHT22 Temperature & Humidity Sensor | 1 |
| Buzzer  | 1 |
| Jumper Wires  | Multiple |
| Breadboard | 1 |

---

## **🔌 Circuit Diagram & Wiring**  

### **📍 DHT22 Sensor to Arduino**  
| **DHT22 Pin**  | **Arduino Pin** |
|---------------|---------------|
| VCC           | **5V**         |
| GND           | **GND**        |
| DATA          | **Pin 5**      |

### **📍 Buzzer to Arduino**  
| **Buzzer Pin** | **Arduino Pin** |
|--------------|----------------|
| + (Positive)  | **Pin 9**      |
| - (Negative)  | **GND**        |

---

## **💻 Arduino Code**  

```cpp
#include <dht.h>

dht DHT;

#define DHT22_PIN 5  // Pin for DHT22 sensor
#define BUZZER 9     // Buzzer pin
#define ATEMP 40     // Temperature threshold for buzzer alert

void setup() {
  Serial.begin(115200);
  pinMode(BUZZER, OUTPUT);
  Serial.println("Humidity (%),\tTemperature (°C)");
}

void loop() {
  // Read data from DHT22 sensor
  DHT.read22(DHT22_PIN);

  // Display humidity and temperature on Serial Monitor
  Serial.print(DHT.humidity, 1);
  Serial.print(",\t\t");
  Serial.print(DHT.temperature, 1);
  Serial.println();

  // Check if temperature exceeds threshold
  if (DHT.temperature > ATEMP) {
    tone(BUZZER, 4699);  // Turn ON buzzer
  } else {
    noTone(BUZZER);  // Turn OFF buzzer
  }

  delay(900); // Delay for data update
}
```

---

## **📷 Project Preview**  
🔹 _Add a photo of your circuit setup here!_  
🔹 **Example:**  
![Project Image](https://your-image-url.com)

---

## **📌 How It Works?**  

1️⃣ Power up the Arduino.  
2️⃣ The **DHT22 sensor** measures **temperature & humidity**.  
3️⃣ The values are **displayed on the Serial Monitor**.  
4️⃣ If **temperature exceeds 40°C**, the **buzzer turns ON**.  
5️⃣ If temperature is **below 40°C**, the **buzzer remains OFF**.  
6️⃣ The system updates readings **every 900ms**.  

---

## **📚 Libraries Used**  
📌 [`dht.h`](https://github.com/adafruit/DHT-sensor-library) - Used for interfacing with the DHT22 sensor.  

---

## **📌 Possible Improvements**  

✅ **Add an LCD Display** to show readings without a PC.  
✅ **Integrate WiFi Module (ESP8266/ESP32)** for remote monitoring.  
✅ **Send Alerts via IoT platforms** like Blynk or ThingSpeak.  
✅ **Use an LED Indicator** for visual overheat alerts.  

---

## **📜 License**  
📝 This project is **open-source** under the **MIT License**. Feel free to **modify and improve!**  

---

## **💬 Support & Contributions**  
⭐ **If you like this project, give it a star on GitHub!**  
👨‍💻 Contributions & pull requests are welcome!  

🚀 **Happy Coding!** 🎯  

---

This **GitHub-optimized README** includes **structured formatting, tables, badges, and clear explanations**. Would you like to add any more features? 🚀
