# VisionTrack-Automatic-Vehicle-Detection-Tracking-Color-Recognition
An OpenCV-based computer vision project that automatically detects a moving vehicle in a video, draws a bounding box around it, isolates it from the background, and identifies its color — all without any manual selection or pre-trained deep learning model.

# 🚗 Real-Time Vehicle Detection and Tracking using OpenCV

A Computer Vision project developed using **Python** and **OpenCV** for real-time vehicle detection and tracking.

The system processes video frames, detects vehicles, identifies their colors, and draws bounding boxes with labels around each detected object.

This project was developed as part of an OpenCV programming assignment.

---

# Features

- Real-time vehicle detection
- Vehicle tracking across video frames
- Vehicle color recognition
- Bounding box visualization
- Object labeling
- Video processing using OpenCV
- Simple and modular Python implementation

---

# Technologies Used

- Python 3
- OpenCV
- NumPy
- Jupyter Notebook

---

# Project Structure

```
Vehicle-Tracking/
│
├── car_tracking.ipynb          # Main notebook
├── processed_output.mp4        # Output video
├── images/
│   ├── white_car.png
│   ├── blue_car.png
│   └── red_car.png
│
├── README.md
└── requirements.txt
```

---

# Sample Results

### White Vehicle Detection

<p align="center">
<img src="images/white_car.png" width="900">
</p>

---

### Blue Vehicle Detection

<p align="center">
<img src="images/blue_car.png" width="900">
</p>

---

### Red Vehicle Detection

<p align="center">
<img src="images/red_car.png" width="900">
</p>

---

# Demo Video

The processed output video is available inside the repository.

📹 **processed_output.mp4**

You can download it directly from the repository and watch the tracking results.

---

# How It Works

1. Read the input video.
2. Process each frame using OpenCV.
3. Detect vehicles in the scene.
4. Extract the dominant vehicle color.
5. Draw a bounding box around each detected vehicle.
6. Display the detected color as the object label.
7. Save the processed video.

---

# Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/Vehicle-Tracking.git
```

Go to the project folder:

```bash
cd Vehicle-Tracking
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

Run the notebook:

```bash
jupyter notebook
```

Open

```
car_tracking.ipynb
```

and run all cells.

---

# Requirements

```
opencv-python
numpy
jupyter
```

or simply install

```bash
pip install -r requirements.txt
```

---

# Future Improvements

- Multi-object tracking
- Vehicle speed estimation
- Vehicle counting
- License plate recognition
- Deep Learning detector (YOLOv8)
- Traffic analytics dashboard

---

# License

This project was created for educational purposes.

---

# Author

**Anas Sami Al-Harithi**
