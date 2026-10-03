# 🪄 Harry Potter Invisibility Cloak using OpenCV

A **Computer Vision project built with Python and OpenCV** that creates a real-time **Harry Potter-style invisibility cloak effect** using a webcam.

The project detects a specific colored cloak using **HSV color segmentation** and replaces the detected cloak region with a previously captured background frame, creating the illusion that the cloak has become invisible.

---

## ✨ Features

* 📷 Real-time webcam processing
* 🪄 Harry Potter-style invisibility effect
* 🎨 Color-based cloak detection
* 🔍 HSV color segmentation
* 🖼️ Background frame capture
* 🎭 Real-time background replacement
* 🎛️ Adjustable HSV values using trackbars
* ⚡ Real-time video processing with OpenCV

---

## 📌 Project Overview

The project creates an invisibility effect by using a simple computer vision technique.

First, the application captures an **empty background frame**. When a person enters the camera view wearing a specific colored cloak, the program detects that color and replaces the cloak region with the corresponding area from the previously captured background.

This makes the cloak appear **invisible**.

### How It Works

```text
                Webcam
                   ↓
            Capture Background
                   ↓
              Live Video
                   ↓
             BGR → HSV
                   ↓
            Color Detection
                   ↓
             Create Mask
                   ↓
        Detect Cloak Region
                   ↓
     Replace Cloak with Background
                   ↓
        🪄 Invisibility Effect
```

---

## 🛠️ Technologies Used

* **Python**
* **OpenCV**
* **NumPy**
* **HSV Color Space**
* **Real-Time Image Processing**

---

## 📂 Project Structure

```text
Harry-Potter-Cloak-using-Open-CV/
│
├── harry_cloak.py
└── README.md
```

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/AyushShrivastava2808/Harry-Potter-Cloak-using-Open-CV.git
```

### 2. Navigate to the Project

```bash
cd Harry-Potter-Cloak-using-Open-CV
```

### 3. Install Dependencies

```bash
pip install opencv-python numpy
```

---

## ▶️ How to Run

Run the Python program:

```bash
python harry_cloak.py
```

Make sure your computer has a working webcam.

---

## 🪄 How to Use

### Step 1 — Start the Program

Run:

```bash
python harry_cloak.py
```

### Step 2 — Capture the Background

When the program starts, **stay out of the camera frame for a few seconds**.

The program captures the empty background and stores it as the reference frame.

```text
Camera
   ↓
Empty Background
   ↓
Background Captured
```

### Step 3 — Wear the Colored Cloak

After the background has been captured, enter the camera frame with a colored cloth.

For the default configuration, a **blue-colored cloth** can be used.

### Step 4 — Move the Cloak

Move the cloak in front of the webcam.

The application detects the cloak's color and replaces that area with the previously captured background.

### Result

The cloak appears to become invisible, creating the Harry Potter-style effect.

---

## 🎛️ HSV Color Controls

The application provides trackbars for adjusting the color detection range:

```text
Upper Hue
Upper Saturation
Upper Value

Lower Hue
Lower Saturation
Lower Value
```

These values can be adjusted according to the color and lighting conditions of the cloak.

---

## 🧠 Computer Vision Concepts Used

### 1. Background Capture

The program first captures an empty frame:

```python
ret, init_frame = cap.read()
```

This frame acts as the background that will later replace the cloak.

---

### 2. BGR to HSV Conversion

The webcam frame is converted from BGR to HSV:

```python
inspect = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)
```

HSV makes color-based segmentation easier.

---

### 3. Color Masking

The cloak color is extracted using:

```python
mask = cv2.inRange(
    inspect,
    lower_hsv,
    upper_hsv
)
```

The mask identifies the pixels belonging to the cloak.

---

### 4. Noise Reduction

A median blur is applied to reduce noise:

```python
mask = cv2.medianBlur(mask, 3)
```

Dilation is also used to improve the detected region:

```python
mask = cv2.dilate(mask, kernel, 5)
```

---

### 5. Mask Inversion

The inverse mask is created:

```python
mask_inv = 255 - mask
```

This allows the program to keep the person/background while removing the detected cloak region.

---

### 6. Background Replacement

The corresponding area from the previously captured background is extracted and combined with the current frame.

Finally:

```python
final = cv2.bitwise_or(
    frame_inv,
    blanket_area
)
```

creates the final invisibility effect.

---

## 🖥️ Application Window

The application provides:

### `bars`

Used to adjust HSV color detection values.

### `Harry's Cloak`

Displays the final real-time invisibility effect.

---

## 📸 Expected Result

With a properly detected colored cloak:

```text
Before:

       👤
      🔵
     🔵🔵
      🔵


After:

       👤
       
     Background
     visible
```

The selected colored cloak region is replaced by the previously captured background.

---

## ⚠️ Important Tips

For the best results:

* Keep the camera stationary.
* Capture the background before entering the frame.
* Use a clearly distinguishable colored cloth.
* Avoid similar colors in the background.
* Use consistent lighting.
* Adjust HSV trackbars if the cloak is not detected.
* Keep the background relatively static.

---

## 🚀 Future Improvements

Possible improvements include:

* 🎨 Automatic color detection
* ✋ Hand/pose detection
* 🧠 AI-based segmentation
* 🎥 Better background modeling
* 🌈 Support for multiple cloak colors
* 📸 Save the final output as a video
* 🖥️ Build a graphical user interface
* 🎭 Real-time background replacement without manual calibration

---

## 🎯 Learning Outcomes

This project helped demonstrate practical implementation of:

* Computer Vision
* OpenCV
* NumPy
* HSV color space
* Image masking
* Morphological operations
* Background subtraction/replacement
* Bitwise image operations
* Real-time video processing

---

## 👨‍💻 Author

**Ayush Shrivastava**

GitHub:
https://github.com/AyushShrivastava2808

---

## ⭐ Support

If you found this project interesting, consider giving the repository a ⭐ on GitHub.

---

## 📄 License

This project is created for educational and learning purposes.
