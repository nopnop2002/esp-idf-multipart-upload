# esp-idf-multipart-upload
A multipart file upload example for esp-idf.

# Server Side
I tested with Tornado & Flask.   
You can choose the one you like.   

## Using Tornado

### Install Tornado
```
sudo apt install python-pip python-setuptools
python -m pip install -U pip
python -m pip install -U wheel
python -m pip install tornado
```

### Start WEB Server using Tornado
```
git clonse https://github.com/nopnop2002/esp8266-multipart
cd esp8266-multipart/tornado
python upload.py
```

---

## Using Flask

### Install Flask
```
sudo apt install python-pip python-setuptools
python -m pip install -U pip
python -m pip install -U wheel
python -m pip install flask
```

### Start WEB Server using Flask
```
git clonse https://github.com/nopnop2002/esp8266-multipart
cd esp8266-multipart/flask
python upload.py
```

---

# ESP32 Side

## Installation
```
git clone https://github.com/nopnop2002/esp-idf-multipart-upload
cd esp-idf-multipart-upload/
make menuconfig
make flash monitor
```

You have to set this config value with menuconfig.

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
This library send this HTTP header.   

```
POST PATH HTTP/1.1
HOST: HOST
User-Agent: esp8266_multipart/1.0
Accept: */*
Content-Type: multipart/form-data; boundary=X-ESP8266_MULTIPART
Content-Length: xxx

--X-ESP8266_MULTIPART
Content-Disposition: form-data; name="uploadFile"; filename="hoge.jpg"
Content-Type: Content-Type: application/octet-stream

binary-data

--X-ESP8266_MULTIPART--
```


