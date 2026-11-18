# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program

### Developed By: Vikamuhan Reddy

### Register No: 212223240181  

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image in grayscale
gray = cv2.imread('parrot.jpg', 0)

# Check whether image is loaded
if gray is None:
    print("Image not found!")
else:
    # Apply histogram equalization
    equalized = cv2.equalizeHist(gray)

    # Display grayscale images and histograms
    plt.figure(figsize=(10, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(gray, cmap='gray')
    plt.title("Original Grayscale Image")
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.hist(gray.ravel(), 256, [0, 256])
    plt.title("Original Histogram")

    plt.subplot(2, 2, 3)
    plt.imshow(equalized, cmap='gray')
    plt.title("Equalized Grayscale Image")
    plt.axis('off')

    plt.subplot(2, 2, 4)
    plt.hist(equalized.ravel(), 256, [0, 256])
    plt.title("Equalized Histogram")

    plt.tight_layout()
    plt.show()

    # Read the image in color
    color = cv2.imread('parrot.jpg')

    # Split B, G, R channels
    b, g, r = cv2.split(color)

    # Plot original color image and its histograms
    plt.figure(figsize=(10, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(cv2.cvtColor(color, cv2.COLOR_BGR2RGB))
    plt.title("Original Color Image")
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.hist(b.ravel(), 256, [0, 256], color='blue', alpha=0.5)
    plt.hist(g.ravel(), 256, [0, 256], color='green', alpha=0.5)
    plt.hist(r.ravel(), 256, [0, 256], color='red', alpha=0.5)
    plt.title("BGR Histograms")

    # Convert BGR to HSV
    hsv = cv2.cvtColor(color, cv2.COLOR_BGR2HSV)

    # Split HSV channels
    h, s, v = cv2.split(hsv)

    # Apply histogram equalization on V channel
    v_equalized = cv2.equalizeHist(v)

    # Merge HSV channels
    hsv_equalized = cv2.merge((h, s, v_equalized))

    # Convert HSV back to BGR
    enhanced = cv2.cvtColor(hsv_equalized, cv2.COLOR_HSV2BGR)

    # Split enhanced image channels
    b2, g2, r2 = cv2.split(enhanced)

    plt.subplot(2, 2, 3)
    plt.imshow(cv2.cvtColor(enhanced, cv2.COLOR_BGR2RGB))
    plt.title("Enhanced Color Image")
    plt.axis('off')

    plt.subplot(2, 2, 4)
    plt.hist(b2.ravel(), 256, [0, 256], color='blue', alpha=0.5)
    plt.hist(g2.ravel(), 256, [0, 256], color='green', alpha=0.5)
    plt.hist(r2.ravel(), 256, [0, 256], color='red', alpha=0.5)
    plt.title("Enhanced BGR Histograms")

    plt.tight_layout()
    plt.show()
```

##  Output

### Grayscale Histogram Equalization

<img width="1018" height="573" alt="image" src="https://github.com/user-attachments/assets/7ab463ba-e0bb-400d-8c06-3d99460227a5" />


### Color Image Histogram Equalization

<img width="1027" height="717" alt="image" src="https://github.com/user-attachments/assets/bdaeeea4-853e-4c46-9dca-0316c0ab45c6" />


---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
