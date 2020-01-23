# HC-SR04 Driver
## Overview
A Mongoose OS library for HC-SR04, a popular ultrasonic distance sensor.
## GET STARTED
Build up your device in few minutes just starting from one of the following samples.

|Sample|Notes|
|--|--|
|[hcsr04-demo](https://github.com/zendiy-mgos/hcsr04-demo)|It shows you how to build a firmware for measuring distances with a HC-SR04 sensor.|
## Usage
Include the library into your `mos.yml` file.
```yaml
libs:
  - origin: https://github.com/zendiy-mgos/hcsr04
```
If you are developing a JavaScript firmware, load `api_hcsr04.js` in your `init.js` file.
```js
load('api_hcsr04.js');
```
## C/C++ API Reference
### mgos_hcsr04_create()
```c
struct mgos_hcsr04 *mgos_hcsr04_create(int trig_pin, int echo_pin);
```
Initialize the sensor instance. Return an opaque sensor's handle, or `NULL` on error.

|Parameter||
|--|--|
|trig_pin|'TRIGGER' GPIO pin.|
|echo_pin|'ECHO' GPIO pin.|

**Example** - Initialize HC-SR04 sensor instance.
```c
struct mgos_hcsr04 *handle = mgos_hcsr04_create(2, 4);
```
### mgos_hcsr04_get_distance()
```c
float mgos_hcsr04_get_distance(struct mgos_hcsr04 *handle);
```
Return distance in millimiters or 'NAN' on failure.

|Parameter||
|--|--|
|handle|Sensor's handle.|

**Example** - Initialize HC-SR04 sensor instance and read the measured distance.
```c
struct mgos_hcsr04 *handle = mgos_hcsr04_create(2, 4);
float distance = mgos_hcsr04_get_distance(handle);
```
### mgos_hcsr04_close()
```c
void mgos_hcsr04_close(struct mgos_hcsr04 *handle);
```
Close the sensor's handle.

|Parameter||
|--|--|
|handle|Sensor's handle.|

**Example** - Initialize HC-SR04 sensor, read the measured distance and then close the instance.
```c
struct mgos_hcsr04 *handle = mgos_hcsr04_create(2, 4);
float distance = mgos_hcsr04_get_distance(handle);
mgos_hcsr04_close(handle);
```
## JS API Reference
