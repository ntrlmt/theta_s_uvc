# Ricoh Theta S UVC ROS Node

Ricoh Theta S ROS node by using uvc(usb video class) 1.1

## Ricoh theta s

https://theta360.com/en/about/theta/s.html

## Ricoh theta doc

https://developers.theta360.com/en/docs/introduction/


## Dependencies
usb_cam package
http://wiki.ros.org/usb_cam

Install
```
sudo apt-get update
sudo apt-get install ros-<distro>-usb-cam
```

## Ricoh theta s UVC info

lsusb -v
```
Bus 003 Device 004: ID 05ca:2711 Ricoh Co., Ltd 
Couldn't open device, some information will be missing
Device Descriptor:
...
  idVendor           0x05ca Ricoh Co., Ltd
  idProduct          0x2711 
```

v4l2-ctl --list-formats-ext
```
    Index       : 1
    Type        : Video Capture
    Pixel Format: 'MJPG' (compressed)
    Name        : Motion-JPEG
        Size: Discrete 960x544
            Interval: Discrete 0.033s (29.970 fps)
            Interval: Discrete 0.040s (25.000 fps)
            Interval: Discrete 0.042s (24.000 fps)
            Interval: Discrete 0.067s (15.000 fps)
        Size: Discrete 1024x576
            Interval: Discrete 0.033s (29.970 fps)
            Interval: Discrete 0.040s (25.000 fps)
            Interval: Discrete 0.042s (24.000 fps)
            Interval: Discrete 0.067s (15.000 fps)
        Size: Discrete 1280x720
            Interval: Discrete 0.033s (29.970 fps)
            Interval: Discrete 0.040s (25.000 fps)
            Interval: Discrete 0.042s (24.000 fps)
            Interval: Discrete 0.067s (15.000 fps)
```

Ricoh theta s spec
```
MotionJPEG
Image size: 1280x720
Frame rate: 15fps
```
https://developers.theta360.com/en/docs/introduction/


## Usage

1. Turn on your ricoh theta with live streaming mode
https://theta360.com/ja/support/manual/s/content/streaming/streaming_01.html
2. Connect your ricoh theta s to your PC usb port
3. Launch
```
roslaunch theta_s_uvc theta_s_uvc_start.launch device:=/dev/video0
```
* With image_view
```
roslaunch theta_s_uvc theta_s_uvc_start.launch device:=/dev/video0 enable_image_view:=true
```