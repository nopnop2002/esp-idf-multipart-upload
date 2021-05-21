# esp-idf-multipart-upload
A multipart file upload example for esp-idf.

# Server Side
Download the server from [here](https://github.com/nopnop2002/multipart-upload-server).

---

# ESP32 Side

## Installation for ESP32
```
git clone https://github.com/nopnop2002/esp-idf-multipart-upload
cd esp-idf-multipart-upload/
idf.py set-target esp32
idf.py menuconfig
idf.py flash
```

## Installation for ESP32S2
```
git clone https://github.com/nopnop2002/esp-idf-multipart-upload
cd esp-idf-multipart-upload/
idf.py set-target esp32s2
idf.py menuconfig
idf.py flash
```

# Configuration   
You have to set this config value with menuconfig.   
- CONFIG_ESP_WIFI_SSID   
SSID of your wifi.
- CONFIG_ESP_WIFI_PASSWORD   
PASSWORD of your wifi.
- CONFIG_ESP_MAXIMUM_RETRY   
Maximum number of retries when connecting to wifi.
- CONFIG_ESP_WEB_SERVER   
IP or DNS of your WEB Server.
- CONFIG_ESP_WEB__PORT   
Port number of your WEB Server.
- CONFIG_ESP_WEB_PATH   
Path of your WEB Server.

![menuconfig-1](https://user-images.githubusercontent.com/6020549/99719529-c07e8700-2aef-11eb-8a11-e5a7aaf2cbd4.jpg)

![menuconfig-2](https://user-images.githubusercontent.com/6020549/99719539-c3797780-2aef-11eb-9cc4-4053c2640434.jpg)

![menuconfig-3](https://user-images.githubusercontent.com/6020549/99719544-c70cfe80-2aef-11eb-8242-9ee855b5c8c2.jpg)

![menuconfig-4](https://user-images.githubusercontent.com/6020549/99719550-c96f5880-2aef-11eb-971d-33eb3cf778a2.jpg)


## About multipart/form-data
This example send this HTTP header.   
If the parameter expected by the server is not "upfile", you need to fix it.   
```
POST PATH HTTP/1.1
HOST: HOST:PORT
User-Agent: esp-idf/X.Y.Z esp32
Accept: */*
Content-Type: multipart/form-data; boundary=X-ESPIDF_MULTIPART
Content-Length: xxx

--X-ESPIDF_MULTIPART
Content-Disposition: form-data; name="upfile"; filename="hoge.jpg"
Content-Type: Content-Type: application/octet-stream

binary-data

--X-ESPIDF_MULTIPART--
```


