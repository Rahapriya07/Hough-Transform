# EXPERIMENT 7 – HOUGH LINE TRANSFORM
## Name : Raha Priya Dharshini M
## Reg No.:212224240124


## Aim
To detect edges and identify straight lines in an image using the Canny Edge Detector and Probabilistic Hough Line Transform in OpenCV.

## Software Requirements
- Python
- OpenCV
- NumPy
- Matplotlib
- Jupyter Notebook

## Procedure
1. Import the required libraries.
2. Read the input image (`myfoto.jpg`) using OpenCV.
3. Convert the original image into a grayscale image.
4. Apply the Canny Edge Detector with threshold values of 50 and 150 to detect edges.
5. Apply the Probabilistic Hough Line Transform using `cv2.HoughLinesP()` to detect line coordinates.
6. Draw the detected lines on the original image using green colour with a thickness of 2.
7. Display the final image containing the detected lines.

## Code:
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image
image = cv2.imread('myfoto.jpg')

if image is None:
    raise FileNotFoundError("myfoto.jpg not found")

# Step 2: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Step 3: Display input image
plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
plt.show()

# Display grayscale image
plt.figure(figsize=(8, 6))
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

# Step 4: Apply Canny edge detection
edges = cv2.Canny(gray_image, 50, 150)

plt.figure(figsize=(8, 6))
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
plt.show()

# Step 5: Apply Probabilistic Hough Line Transform
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)

# Step 6: Draw detected lines
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)
else:
    print("No lines detected")

# Step 7: Display Hough Transform result
plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
plt.show()
```


## Output

### 1. Original Input Image
<img width="1365" height="555" alt="image" src="https://github.com/user-attachments/assets/7842449e-5ccf-4a9a-a1f7-7080845d4dec" />


### 2. Grayscale Image
<img width="1351" height="546" alt="image" src="https://github.com/user-attachments/assets/2e608cfb-32a8-4dd5-b6f4-156be34cbae2" />


### 3. Canny Edge Detection
<img width="1355" height="553" alt="image" src="https://github.com/user-attachments/assets/b4304b38-a1b5-467d-a071-1cd5bd264898" />


### 4. Hough Line Transform
<img width="1355" height="545" alt="image" src="https://github.com/user-attachments/assets/b876bbff-ca3d-44dd-acea-11b47fd7da17" />


## Result
Thus, edge detection and straight-line detection were successfully performed using the Canny Edge Detector and Probabilistic Hough Line Transform in Python with OpenCV.
