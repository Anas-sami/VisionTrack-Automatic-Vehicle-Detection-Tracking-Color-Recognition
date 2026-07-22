# VisionTrack-Automatic-Vehicle-Detection-Tracking-Color-Recognition
An OpenCV-based computer vision project that automatically detects a moving vehicle in a video, draws a bounding box around it, isolates it from the background, and identifies its color — all without any manual selection or pre-trained deep learning model.


# 🚗 Real-Time Vehicle Detection and Tracking using OpenCV

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green?style=for-the-badge&logo=opencv)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

### A Computer Vision project for detecting, tracking, and recognizing vehicle colors in real-time using OpenCV.

</div>

---

# 📖 About the Project

This project demonstrates how Computer Vision techniques can be used to detect and track moving vehicles in a video stream.

Using the OpenCV library, the system analyzes each frame, identifies vehicles, tracks their movement, recognizes their dominant color, and displays the results with bounding boxes and labels in real time.

The primary objective of this project is to explore practical applications of image processing and object tracking while building a simple yet effective intelligent vision system.

---

# ✨ Features

- 🚗 Real-time vehicle detection
- 🎯 Vehicle tracking across video frames
- 🎨 Vehicle color recognition
- 📦 Bounding box visualization
- 🏷️ Automatic object labeling
- 🎥 Video processing and output generation
- 🧩 Clean and modular implementation

---

# 🛠️ Technologies Used

- Python 3
- OpenCV
- NumPy
- Jupyter Notebook

---

# 📂 Project Structure

```
Vehicle-Tracking/
│
├── car_tracking.ipynb
├── processed_output.mp4
├── requirements.txt
├── README.md
│
└── images/
    ├── white_car.png
    ├── blue_car.png
    └── red_car.png
```

---

# 🖼️ Detection Results

## White Vehicle

<p align="center">
<img src="images/white_car.png" width="900">
</p>

---

## Blue Vehicle

<p align="center">
<img src="images/blue_car.png" width="900">
</p>

---

## Red Vehicle

<p align="center">
<img src="images/red_car.png" width="900">
</p>

---

# 🎥 Demo Video

The processed output video is included in this repository.

▶️ **Watch the result here**

[processed_output.mp4](processed_output.mp4)

---

# ⚙️ How It Works

The workflow of the system is straightforward:

1. Read the input video.
2. Process every frame individually.
3. Detect the vehicle.
4. Track the detected object.
5. Identify the vehicle color.
6. Draw a bounding box around the vehicle.
7. Display the detected color as a label.
8. Save the processed video.

---

# 🚀 Getting Started

Clone the repository

```bash
git clone https://github.com/your-username/Vehicle-Tracking.git
```

Move into the project directory

```bash
cd Vehicle-Tracking
```

Install the required packages

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook

```bash
jupyter notebook
```

Open

```
car_tracking.ipynb
```

Run all notebook cells to reproduce the results.

---

# 📦 Requirements

```
opencv-python
numpy
jupyter
```

Install everything using

```bash
pip install -r requirements.txt
```

---

# 💡 Future Improvements

Although this project successfully demonstrates vehicle tracking, it can be further enhanced by adding:

- Multiple vehicle tracking
- Vehicle counting
- Speed estimation
- License plate recognition
- YOLOv8-based object detection
- Traffic analytics dashboard

---

# 📸 Project Preview

This project detects vehicles and recognizes their colors in real time while drawing bounding boxes around the detected objects.

The output demonstrates accurate tracking and clear visualization, making it suitable as a beginner-to-intermediate Computer Vision project using OpenCV.

---

# 📄 License

This project was developed for educational purposes as part of an OpenCV programming assignment.

---

<div align="center">

## 👨‍💻 Author

### **Anas Sami Al-Harithi**

Computer Science Student

**Thank you for visiting this project.**

⭐ If you found this project helpful, feel free to give it a star.

</div>
