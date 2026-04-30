🏎️ AI Traffic Monitor: 

Speed Detection with Depth CorrectionThis repository contains a high-precision vehicle speed detection system.
By combining YOLOv8 for object detection, ByteTrack for multi-object tracking,
and a custom Perspective Transformation engine, this system converts raw video pixels into real-world velocity data (km/h).

🌟 Key Features

Real-Time Tracking: Uses ByteTrack to maintain unique vehicle IDs across frames.

Perspective Transformation: Maps 2D camera pixels to a "Bird’s Eye View" for accurate distance measurement.

Dynamic Depth Correction: A custom exponential scaling algorithm that compensates for perspective distortion in the distance.

Automated Snapshot Enforcement: Automatically crops and saves images of vehicles exceeding the speed limit.

Visual Analytics: Real-time motion traces and color-coded alerts (Normal vs. Speeding).

link of data used [https://drive.google.com/drive/folders/1dW2hHezYkvkvyZwwIbY5NdZn8V7rWhDm?usp=sharing]
