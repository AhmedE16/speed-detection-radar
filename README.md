AI-Powered Traffic Monitoring & Automated Speed Enforcement System

1-Project Overview
This project implements an intelligent traffic surveillance system designed to detect, track, and calculate the real-world speed of vehicles using a monocular camera feed. By combining Computer Vision (YOLOv8) with Geometrical Perspective Transformation, the system transforms raw video pixels into actionable traffic data. Unlike standard speed-estimation scripts, this system includes a custom Depth Correction Algorithm to compensate for perspective distortion in high-angle camera placements.

2-Core Methodologies
   
A. Object Detection & Multi-Object Tracking (MOT)The system utilizes YOLOv8x (You Only Look Once) for high-accuracy vehicle localization. To maintain the identity of vehicles across frames, it employs ByteTrack, which allows the system to calculate displacement over time for individual vehicles rather than just detecting them in isolation.

B. Perspective Transformation & Coordinate MappingStandard cameras capture a trapezoidal view of the road where distant objects appear smaller. To calculate speed, the system maps these image coordinates $(x, y)$ to a top-down "Bird’s Eye View" $(X, Y)$ representing real-world meters. This is achieved using a Homography Matrix derived from known road dimensions.

C. The Depth Correction FormulaA significant challenge in traffic monitoring is "perspective stretching," where movement in the distance is mathematically amplified. The system applies a dynamic correction factor based on the vertical position ($y$-coordinate) of the vehicle:$$depth\_correction = 0.2 + (0.8 \times normalized\_y^2)$$This ensures that speed readings remain consistent whether the vehicle is 10 meters or 100 meters away from the camera.

3-Key System Features
Real-Time Velocity Estimation: Calculates speed in $km/h$ by measuring the Euclidean distance moved in transformed space over a specific time delta ($dt$).

Temporal Smoothing: Implements a rolling average (Smoothing Window) to filter out "noise" or jitter in the AI’s bounding box detections, providing a stable speed reading.Automated Enforcement (Snapshot System): When a vehicle's speed exceeds a predefined threshold (e.g., $90 km/h$), the system triggers an "Alert State." It automatically crops the vehicle from the frame and saves a high-resolution snapshot with the ID and speed timestamped for evidence.

Visual Analytics: The output video features dynamic annotations, including "motion traces" (showing the vehicle's path) and color-coded bounding boxes (Red for speeders, Blue for normal traffic).

4-Technical StackLanguage: PythonAI Framework: Ultralytics YOLOv8Vision Libraries: OpenCV, Supervision (by Roboflow)Mathematics: NumPy (Linear Algebra & Matrix Transformations)Processing: TQDM (Progress Tracking) and VideoSink for frame-by-frame encoding.

5-Potential ApplicationsSmart
City Infrastructure: Automated traffic flow analysis.
Law Enforcement: Unmanned speed trap deployments.
Highway Safety: Real-time detection of reckless driving or illegal stopping.
