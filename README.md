2014-05-a.stereo
================

Oculus and OVR using gstreamer

================
Some useful stuff on the path to stereo vision

GStreamer can do a lot. It's pipelines look like this when contructed 
[src]  !  [sink  src]  !  [sink  src]  !  [sink]

Forks are pretty eaxy, muxing audio and video, multiple audio etc. 

We need to be streaming both cameras side by side. 

To make sure gstreamer is installed you should be able to run this. And get the webcame coming up in x 

gst-launch v4l2src device=/dev/video0 ! \
video/x-raw-yuv,width=640,height=480,framerate=30/1 ! \
ffmpegcolorspace ! video/x-raw-rgb \! ximagesink

Smashing a sobel edge detect is kind of fun. 

gst-launch v4l2src device=/dev/video0 ! \
video/x-raw-yuv,width=640,height=480,framerate=30/1 ! \
ffmpegcolorspace ! video/x-raw-rgb \! edgetv ! ximagesink


