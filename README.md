# Streaming video from ZED2 camera

Hardware: Nvidia AGX Xavior, ZED2..
Software: Docker, ZED SDK..

## With ROS

It's possible to read from a ROS topic then forward that data to a website with the following lib:
https://github.com/RobotWebTools/web_video_server
Unsure if this implementation uses the hardware accelerated encode/decode mechanism that Nvidia uses, most likely
not
We also have(images and not videostream):
https://github.com/ros-drivers/video_stream_opencv

 
## Without ROS 2

Nvidia's multimedia support covers both encode/decode to h.264, via gstreamer see following link:
https://docs.nvidia.com/jetson/l4t/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/multimedia.html#

Here is an example of it being used: 
https://forums.developer.nvidia.com/t/display-zed-camera-stream-to-gstreamer/190257/5

´´´
gst-launch
´´´

Nvidia's own samples using encoding and decoding
https://github.com/NVIDIA/video-sdk-samples

Flask + OpenCV
https://github.com/NakulLakhotia/Live-Streaming-using-OpenCV-Flask
+RTSP server

Zed's own examples, uses h264 encoding by default, streams to a given port
https://github.com/stereolabs/zed-examples



## Proposed solution

Use gstreamer on the Jetson device which is hardware accelerated, side-stepping ros2 and use ros2 for odrive control.
Well, how can we display the video? Simple GUI? Web? The fastest option, in terms of achieveing low-latency.



