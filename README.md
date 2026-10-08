# ROS AI HAT+

A ROS2 workspace containing packages that perform inference on the AI HAT+ (Compatible with Raspberry Pi 5)
Falls back to CPU inference if the AI HAT+ is not present.

- You'll have to manually set this.

## Setup

```bash
sudo apt install python3-opencv python3-numpy ros-jazzy-cv-bridge ros-jazzy-vision-msgs
pip install onnxruntime --break-system-packages
```

`onnxruntime` isn't a rosdep-resolvable key, hence the separate `pip install`
rather than `rosdep install` picking it up automatically.

Build Packages:

```bash
colcon build
source install/setup.bash
```

## CPU-native Inference

```bash
ros2 launch cpu_yolo_detector cpu_detector.launch.py \
  model_path:=/path/to/yolov8s.onnx \
  input_topic:=/camera/image_raw
```
