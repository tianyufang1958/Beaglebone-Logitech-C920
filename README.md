# Beaglebone-Logitech-C920
Beaglebone black vision with Logitech  C920 and v4l2

The cheap webcam can only output YUYV pixel format, which is an uncompressed format. Besides this format, Logitech C920 can also output MJPG and H264 formats, both of which are compressed format. Due to the bandwidth of Beaglebone usb, YUYV video is too heavy even with the resolution lower than 640 x 480. 

Video4Linux (v4l) is a vidwo capture and output device API an driver framework for the Linux kernel, supporting many USB webcams and v4l2 is the second version of v4l. v4l2 can be installed by the command 

sudo apt-get install v4l-utils

and the parameter of webcam can be configured by v4l2:

uname -a
lsusb
ls /dev (/dev/video0 should appear once the webcam is plug in, but if you replug in again, it may change to /dev/video1)
v4l2-ctl --list -devices (list all the webcam devices)
v4l2-ctl -d /dev/video0/ --all (specify the devices and list all parameters)
v4l2-ctl --set-ctrl=brightness=200
v4l2-ctl --list-formats
v4l2-ctl --set-fmt-video-width=1920,height=1080,pixelformat=1 (set to H264 format)
