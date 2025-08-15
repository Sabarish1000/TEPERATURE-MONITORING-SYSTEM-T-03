# TEPERATURE-MONITORING-SYSTEM-T-03
A simple Arduino-based Temperature Monitoring System using a DHT11 sensor and I2C LCD. Continuously measures temperature and displays it on the LCD. Simulated using Wokwi Online Simulator for easy testing before hardware deployment.

# Temperature Monitoring System

##  Overview
This project is a **Temperature Monitoring System** built using **Arduino Uno**, **DHT11 temperature sensor**, and an **I2C LCD display**.  
It continuously reads temperature values from the sensor and displays them in Celsius.  
The system is simulated using **Wokwi Online Simulator** for testing before real-world implementation.

## Hardware Requirements
- Arduino Uno R3
- DHT11 Temperature Sensor
- I2C LCD 16x2 Display
- Jumper Wires

## Software Requirements
- Arduino IDE
- Wokwi Online Simulator (optional)
- Libraries:
  - `Wire.h`
  - `LiquidCrystal_I2C.h`
  - `DHT.h`



## Circuit Description
- **DHT11 Sensor** → Digital pin D2
- **I2C LCD** → SDA (A4), SCL (A5)
- LCD displays real-time temperature in Celsius

## Arduino Code
```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  lcd.init();
  lcd.backlight();
  dht.begin();
  lcd.setCursor(0, 0);
  lcd.print("Temperature:");
}

void loop() {
  float temp = dht.readTemperature();
  lcd.setCursor(0, 1);
  lcd.print(temp);
  lcd.print(" C");
  delay(2000);
}

**The project was tested using Wokwi:
**
Arduino Uno + DHT11 + I2C LCD connected virtually

Simulated temperature readings displayed in Celsius

Output refreshed every 2 seconds
Project Link: //wokwi.com/projects/437828008599742465

**Applications
**Weather stations
Industrial monitoring
Agriculture
Home automation
