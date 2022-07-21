# script code
import time
import board
import adafruit_dht
import psutil

for proc in psutil.process_iter():
    if proc.name() == 'libgpiod_pulsein' or proc.name() == 'libgpiod_pulsei':
        proc.kill()
sensor = adafruit_dht.DHT11(board.D23)
while True:
    try:
        temp = sensor.temperature
        humidity = sensor.humidity
        print("Temperature: {}*C   Humidity: {}% ".format(temp, humidity))
    except RuntimeError as error:
        print(error.args[0])
        time.sleep(2.0)
        continue
    except Exception as error:
        sensor.exit()
        raise error
    time.sleep(2.0)
   
# wiring diagram

![IMG-20220721-WA0009](https://user-images.githubusercontent.com/107297085/180228794-b2fabfb0-5dcf-49da-b3ca-7f5458a67c1e.jpg)

# data dari sensor

![2022-07-15-134600_1366x768_scrot](https://user-images.githubusercontent.com/107297085/180229124-50eeac70-f411-46a3-ae0f-6a8ff46aa9ea.png)

![2022-07-15-134846_1366x768_scrot](https://user-images.githubusercontent.com/107297085/180229588-51c13118-1726-4067-8f7e-78975c8236dd.png)

# grafik 

![2022-07-15-135933_1366x768_scrot](https://user-images.githubusercontent.com/107297085/180229836-9597fce0-b48c-47c2-a7d6-bb7227a43efa.png)
