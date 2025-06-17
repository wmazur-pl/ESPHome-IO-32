# ESPHome 32-Channel Controller – ESP32-S3 + W5500 + MCP23017

This project provides an ESPHome configuration for an advanced home automation controller based on the ESP32-S3 with Ethernet (W5500), 32 relay outputs, digital inputs, and a variety of sensors.

## Features

- **32 relay outputs** via two MCP23017 expanders (`0x20`, `0x21`)
- **32 button inputs** via two MCP23017 expanders (`0x22`, `0x23`)
- **8 digital inputs** (GPIO1–GPIO8, IN33–IN40) with opto-isolation
- **Ethernet LAN** using W5500 (SPI3)
- **2.4" TFT display** (ILI9341)
- **Touch screen controller** on separate SPI with CS and IRQ
- **Piezo buzzer** on GPIO46
- **Real-time clock (RTC)** DS3231 (I2C, `0x68`)
- **FRAM memory** (I2C, `0x50`)
- **Analog input converter** ADS1115 (I2C, `0x48`)
- **Temperature sensor** LM75 (I2C, `0x49`)
- **Voltage/Current monitor** INA226 (I2C, `0x45`)
- **Multiple DS18B20 sensors supported via two separate OneWire buses** (OneWire buses)
- **RF433 receiver (SYN480)** on GPIO21

## Pinout

### W5500 – SPI3 (Ethernet)
- **MOSI**: GPIO12 
- **MISO**: GPIO11  
- **CLK**: GPIO10  
- **CS**: GPIO9  
- **IRQ**: GPIO13  
- **RESET**: GPIO14  

### I2C Bus (Sensors and Expanders)
- **SDA**: GPIO47  
- **SCL**: GPIO48  

### TFT Display – ILI9341 (Dedicated SPI Bus)
- **MOSI**: GPIO41  
- **MISO**: GPIO40  
- **CLK**:  GPIO42  
- **CS**:   GPIO39  
- **RST**:  GPIO17  
- **LED**:  GPIO45  

### Touch Controller (for TFT)
- **Touch CS**: GPIO15  
- **Touch IRQ**: GPIO16  

### Other GPIOs
- **BUZZER**: GPIO46  
- **Digital Inputs**: GPIO1–GPIO8 (IN33–IN40)  
- **RF433 Receiver (SYN480)**: GPIO21  
- **DS18B20 OneWire**:  
  - Bus 1: GPIO19  
  - Bus 2: GPIO20  

## Dallas Temperature Sensor Example

We are using two OneWire buses:

```yaml
sensor:
  - platform: dallas_temp
    name: "DS18B20-1"
    one_wire_id: onewire_bus_1
    address: 0x1C0000031BACFF28

  - platform: dallas_temp
    name: "DS18B20-2"
    one_wire_id: onewire_bus_2
    address: 0x2D0000041CDAFF29
```