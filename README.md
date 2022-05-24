# YTS
from math import floor
from adafruit_rplidar import RPLidar

PORT_NAME = "/dev/ttyUSB0"
lidar = RPLidar(None, PORT_NAME, timeout=3)

max_distance = 0

def process_data(data):
    print(data)

scan_data = [0] * 360

try:
    for scan in lidar.iter_scans():
        for (_, angle, distance) in scan:
            print(angle)
            print(distance)
        
except KeyboardInterrupt:
    print("Stopping.")
lidar.stop()
lidar.disconnect()
