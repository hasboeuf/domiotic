# restforgpio

Tired to upload a sketch everytime you need to interact with a GPIO? This sketch is pretty useful at development time when nothing is decided permanently.

## Requirements

* ESP8266 like this [one](https://fr.aliexpress.com/item/V2-4M-4FLASH-NodeMcu-Lua-WIFI-Networking-development-board-Based-ESP8266/32647690484.html)
* Change the WIFI settings of the sketch to fit yours.
* Set a permanent IP address for the MAC address of the WIFI ship
* [ESP8266WiFi lib](https://arduino-esp8266.readthedocs.io/en/latest/esp8266wifi/readme.html)
* [Regex lib](https://github.com/nickgammon/Regexp)
* [ArduinoJson lib](https://arduinojson.org/)

## API

Mostly documented itself on the `/` endpoint.

```bash
curl <ip>/
{
  "endpoints": [
    "GET ^/$",
    "GET ^/status$",
    "GET ^/gpio$",
    "GET ^/gpio/(%d+)$",
    "PUT ^/gpio/(%d+)/value/(%a+)$",
    "PUT ^/gpio/(%d+)/mode/(%a+)$",
    "PUT ^/restart$"
  ]
}
```

By default all GPIO are in INPUT mode. The API allows you to change this dynamically.

There are basically 9 GPIO on the board (from D0 to D8). to switch up GPIO 3, just do this:

```bash
curl -X PUT <ip>/3/mode/output
curl -X PUT <ip>/3/value/high
```

Also a postman collection is available to show all possibilities.
