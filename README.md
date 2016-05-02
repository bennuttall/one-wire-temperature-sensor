# One-wire temperature sensor

How to use the one-wire temperature sensor in CamJam Kit 2

## Wiring

![](http://www.raspberrypi-spy.co.uk/wp-content/uploads/2013/03/DS18B20-Temperature-Sensor_bb.png)

Note: the default is to use GPIO pin 4. See the note below if you need to use another pin.

## Enable software

1. Open **Raspberry Pi Configuration Tool** from the Main Menu, under Preferences

1. Select the **Localisation** tab

1. Select **Enable** under **One wire temperature sensor**

Note: using GPIO pin 4 requires no further configuration. If using this pin is not an option, you'll need to amend the following line in `/boot/config.txt`:

```
dtoverlay=w1-gpio
```

should become:

```
dtoverlay=w1-gpio,gpiopin=21
```

(for example, to use GPIO pin 21)

## Install library

Open a Terminal window and type:

```bash
sudo apt-get update
sudo apt-get install python-w1thermsensor python3-w1thermsensor  -y
```

## Python code

The following code will print the temperature value:

```python
from w1thermsensor import W1ThermSensor

sensor = W1ThermSensor()

temp = sensor.get_temperature()

print(temp)
```

## GPIO Zero

There is a plan to add this sensor to the GPIO Zero library. It is expected in v1.3. See [GitHub Issue #93](https://github.com/RPi-Distro/python-gpiozero/issues/93) for updates.
