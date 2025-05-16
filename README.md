# ESPHome 32-Channel Controller – ESP32-S3 + W5500 + MCP23017

Projekt konfiguracji ESPHome dla rozbudowanego sterownika automatyki domowej opartego o ESP32-S3 z Ethernetem (W5500), 32 przekaźnikami (MCP23017), wejściami cyfrowymi i szeregiem czujników.


## Funkcje sterownika

- 32 wyjścia przekaźnikowe sterowane przez 2 ekspandery MCP23017 (`0x20`, `0x21`)
- 32 wejścia przyciskowe przez MCP23017 (`0x22`, `0x23`)
- 8 wejść cyfrowych bezpośrednio na GPIO (IN33–IN40, GPIO1–GPIO8, optoizolacja)
- Ethernet LAN przez W5500 (SPI3)
- TFT 2.4" ILI9341
- Buzzer (GPIO46)
- Zegar czasu rzeczywistego (DS3231)
- Pamięć FRAM (0x50)
- Wejścia analogowe przez ADS1115 (0x48)
- Pomiar temperatury (LM75 – 0x49)
- Pomiar napięcia/prądu (INA226 – 0x45)
- Obsługa 2 czujników DS18B20 (GPIO19, GPIO20)


## Pinout

### W5500 – SPI3 (Ethernet)
- MOSI: GPIO11  
- MISO: GPIO12  
- CLK: GPIO10  
- CS: GPIO9  
- IRQ: GPIO13  
- RESET: GPIO14  

### I2C – czujniki i ekspandery
- SDA: GPIO47  
- SCL: GPIO48  

### TFT ILI9341
- MOSI: GPIO41  
- MISO: GPIO40  
- CLK:  GPIO42  
- CS:   GPIO39  
- RST:  GPIO17  
- LED:  GPIO45  

### Inne
- BUZZER: GPIO46  
- Wejścia cyfrowe: GPIO1–GPIO8 (IN33–IN40)
- DS18B20: GPIO19 i GPIO20