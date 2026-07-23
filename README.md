# Experiment 1 — Image Scaling and Rotation from Scratch

Custom implementation of **image scaling** and **image rotation**, each using
**Nearest Neighbour** and **Bilinear** interpolation, built without relying on
OpenCV's built-in transformation functions.

## 📌 Objective

To develop a Python program that reads an image and performs image scaling and
rotation using custom-implemented functions.

## ⚙️ Constraints

- OpenCV (`cv2`) is used **only** to read the input image and write the output
  images.
- Scaling, rotation, and both interpolation methods (Nearest Neighbour and
  Bilinear) are implemented **from scratch** using NumPy.

## 🧠 Methodology

1. **Image Acquisition** — Read the input image with OpenCV/PIL and convert
   it to grayscale.
2. **Scaling** — Implement scaling using:
   - Nearest Neighbour interpolation
   - Bilinear interpolation
3. **Rotation** — Implement rotation about the image centre using:
   - Nearest Neighbour interpolation
   - Bilinear interpolation
4. **Output** — transformed images

Each transformation uses **inverse (backward) mapping**: for every pixel in
the output image, the corresponding source coordinate is computed, and its
intensity is estimated via the chosen interpolation scheme. This avoids the
holes/gaps that forward mapping can leave in the output image.



## 🖼️ Sample Results

| Transformation | Nearest Neighbour | Bilinear |
|---|---|---|
| Scaling (factor = 2) | [Scaling nearest Neighbour](output/scaleopnear_neigh.jpg) | [Scaling Bilinear](output/scaleop_bilinear.jpg) |
| Rotation (θ = 45°) | [Rotation Nearest Neighbour](rotateop_nearest.jpg) | [Rotation Bolinear](rotateop_bilinear.jpg) |





## 🔑 Key Concepts

- **Inverse Mapping** — Output-to-source coordinate mapping used to avoid
  unfilled pixels in the transformed image.
- **Nearest Neighbour Interpolation** — Assigns the intensity of the closest
  source pixel; fast but can look blocky/aliased.
- **Bilinear Interpolation** — Weighted average of the 4 nearest source
  pixels; smoother output at a higher computational cost.
- **Rotation about centre** — Coordinates are shifted to the image centre
  before applying the (inverse) rotation matrix, then shifted back, so the
  image rotates about its middle rather than the top-left corner.

## 🛠️ Tech Stack

- Python 3
- NumPy — array operations and transformation math
- OpenCV (`cv2`) — image I/O only
- Pillow (`PIL`) — image loading/grayscale conversion
- Matplotlib — visualization

## 👤 Author

Dharmik Patel
MTech, Vision and Intelligent System, IIT Kharagpur
