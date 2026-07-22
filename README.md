# VisionTrack-Automatic-Vehicle-Detection-Tracking-Color-Recognition
An OpenCV-based computer vision project that automatically detects a moving vehicle in a video, draws a bounding box around it, isolates it from the background, and identifies its color — all without any manual selection or pre-trained deep learning model.



> **Category:** Object Tracking (with an integrated Color Recognition module)
> **Built with:** Python, OpenCV, NumPy

---

## Demo

The system was tested on a video containing three completely different scenes (a white sedan, a black SUV, and a red Ferrari), each with a professionally blurred (bokeh) background. In every scene, the system detects the vehicle from scratch, draws a bounding box around its full body, grays out the background, and labels it with its correct color — with no manual input required.

| White Sedan | Black SUV | Red Ferrari |
|:---:|:---:|:---:|
| ![White sedan detected and labeled](assets/screenshot_1_sedan.png) | ![Black SUV detected and labeled](assets/screenshot_2_suv.png) | ![Red Ferrari detected and labeled](assets/screenshot_3_ferrari.png) |

A full processed video demo is included at [`assets/demo_video.mp4`](assets/demo_video.mp4).

---

## The Problem

Most beginner object-tracking tutorials rely on one of two approaches, both of which break down quickly in real footage:

1. **Fixed HSV color-range thresholding** — fails the moment lighting changes, or any other object in the frame happens to share a similar hue.
2. **Single-object trackers (KCF/CSRT) with manual ROI selection** — only follow the one object initially selected, and fail completely the instant the video cuts to a different scene or a different vehicle.

This project needed something that works automatically, frame by frame, regardless of how many scene cuts or vehicles appear in the footage — with no manual intervention and no external dataset or pre-trained model.

---

## The Approach

The footage used here is produced with a shallow depth of field: the vehicle is always in sharp focus while the background is intentionally blurred. This project exploits that property directly instead of relying on color or a single tracked ROI.

**Pipeline, per frame:**

1. **Focus-based segmentation** — A Laplacian filter measures local sharpness across the frame. Since the background is optically blurred and the vehicle is in focus, this naturally separates the two regions without needing any color assumptions.
2. **Morphological cleanup** — Otsu thresholding converts the sharpness map into a binary mask, followed by closing and opening operations to merge nearby sharp regions (wheels, grille, window frames) into a single solid blob and remove small noise (road markings, small logos).
3. **Bounding box padding** — Smooth, uniformly painted body panels (hoods, doors, roofs) naturally produce very little edge energy even though they are perfectly in focus, so the raw sharp-region contour tends to undershoot the vehicle. A calibrated padding margin is added around the detected region to guarantee the full vehicle — roof, bumper, and wheels — is enclosed.
4. **Background isolation** — Everything outside the final bounding box is converted to grayscale, while the vehicle itself stays in full color, producing a clean "spotlight" effect.
5. **Color recognition** — A center crop of the bounding box is sampled in HSV color space (avoiding the box edges, which can contain background or reflections). The system first determines whether the vehicle is achromatic (white / gray / black) or chromatically colored, since each requires a different classification strategy:
   - **Achromatic vehicles** are classified by the 80th-percentile brightness value, which is more robust to shadows and dark window glass than a plain average.
   - **Chromatically colored vehicles** are classified using the peak of a hue histogram (computed only on sufficiently saturated pixels), which is far more robust than a simple mean/median — especially for hues like red that wrap around the 0°/180° boundary in HSV.
6. **Labeling** — The final bounding box and detected color name are drawn directly onto the frame.

---

## Features

- Fully automatic — no manual ROI selection, no clicking, no pre-trained model
- Works across multiple scene cuts and multiple vehicles in the same video
- Robust color detection that correctly distinguishes white/gray/black vehicles from chromatically colored ones
- Background isolation (grayscale background, full-color vehicle) for a clean visual effect
- Lightweight — only depends on OpenCV and NumPy, no GPU or deep learning framework required

---

## Requirements

```
pip install opencv-python numpy
```

## Usage

1. Open `vehicle_tracker.py` and set your input/output paths:

```python
video_path = r"path/to/your/input_video.mp4"
output_path = r"path/to/your/output_video.mp4"
```

2. Run the script:

```
python vehicle_tracker.py
```

The processed video will be written to `output_path`, with each frame showing the detected vehicle, its bounding box, and its recognized color.

An equivalent, cell-by-cell walkthrough is also provided in [`car_tracking.ipynb`](car_tracking.ipynb) for anyone who prefers to run it interactively in Jupyter.

---

## Project Structure

```
.
├── vehicle_tracker.py      # Main script
├── car_tracking.ipynb      # Jupyter notebook version
├── assets/
│   ├── demo_video.mp4      # Sample processed output
│   ├── screenshot_1_sedan.png
│   ├── screenshot_2_suv.png
│   └── screenshot_3_ferrari.png
└── README.md
```

## Configuration

A few constants at the top of `vehicle_tracker.py` can be tuned for different footage:

| Parameter | Purpose |
|---|---|
| `MIN_AREA_RATIO` | Minimum contour area (relative to frame size) to be considered a real object, filtering out noise |
| `PAD_LEFT` / `PAD_RIGHT` / `PAD_TOP` / `PAD_BOTTOM` | Padding margins added around the detected sharp region to ensure full vehicle coverage |

## Limitations & Future Work

- The focus-based segmentation assumes a blurred background (shallow depth of field). It is not designed for footage with an in-focus background.
- Detection currently returns a single largest object per frame; extending it to track multiple vehicles simultaneously would require multi-blob handling.
- Color classification uses a fixed HSV rule set; replacing it with a small trained classifier could improve accuracy on edge-case paint colors (e.g., metallic or two-tone finishes).

---

## Author

**Anas Sami Al-Harithi**
