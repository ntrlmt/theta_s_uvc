# Ricoh Theta S UVC ROS Node

Ricoh Theta S ROS node by using uvc(usb video class) 1.1

## Ricoh Theta S
https://theta360.com/en/about/theta/s.html

## Ricoh Theta Doc
https://developers.theta360.com/en/docs/introduction/


## Dependencies
usb_cam package
http://wiki.ros.org/usb_cam

Install
```
sudo apt-get update
sudo apt-get install ros-<distro>-usb-cam
```

## Ricoh Theta S UVC info

Install v4l2-ctl command
```bash
sudo apt-get install v4l-utils
```


$ v4l2-ctl --list-devices
```
RICOH THETA S: RICOH THETA S (usb-0000:00:14.0-3):
	/dev/video0
	/dev/video1
```

Select first device (ex. /dev/video0)

$ v4l2-ctl -d /dev/video0 --all
```
Driver Info (not using libv4l2):
	Driver name   : uvcvideo
	Card type     : RICOH THETA S: RICOH THETA S
	Bus info      : usb-0000:00:14.0-3
	Driver version: 5.3.18
	Capabilities  : 0x84A00001
		Video Capture
		Metadata Capture
		Streaming
		Extended Pix Format
		Device Capabilities
	Device Caps   : 0x04200001
		Video Capture
		Streaming
		Extended Pix Format
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
	Width/Height      : 1280/720
	Pixel Format      : 'MJPG'
	Field             : None
	Bytes per Line    : 0
	Size Image        : 4147200
	Colorspace        : sRGB
	Transfer Function : Default (maps to sRGB)
	YCbCr/HSV Encoding: Default (maps to ITU-R 601)
	Quantization      : Default (maps to Full Range)
	Flags             : 
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 1280, Height 720
	Default     : Left 0, Top 0, Width 1280, Height 720
	Pixel Aspect: 1/1
Selection: crop_default, Left 0, Top 0, Width 1280, Height 720
Selection: crop_bounds, Left 0, Top 0, Width 1280, Height 720
Streaming Parameters Video Capture:
	Capabilities     : timeperframe
	Frames per second: 14.985 (2997/200)
	Read buffers     : 0
```


$ v4l2-ctl -d /dev/video0 --list-formats-ext
```
ioctl: VIDIOC_ENUM_FMT
	Index       : 0
	Type        : Video Capture
	Pixel Format: 'MJPG' (compressed)
	Name        : Motion-JPEG
		Size: Discrete 1280x720
			Interval: Discrete 0.067s (14.985 fps)
```

Ricoh theta s spec
```
MotionJPEG
Image size: 1280x720
Frame rate: 15fps
```  


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

## Known Issues

### ros usb_cam

Below warning message shows, but you can ignore it.

```
deprecated pixel format used, make sure you did set range correctly
```

https://github.com/ros-drivers/usb_cam/issues/109