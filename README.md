
# Bilateral Filter

## Explanation
The Bilateral filter is a non-linear filter used for edge-preserving smoothing. It reduces noise while preserving edges by considering both the spatial distance and intensity difference between pixels.

## How It Works
1. **Bilateral Filter Equation**:
   $$
   I_{\text{filtered}}(i, j) = \frac{1}{W_p} \sum_{k,l} I(k, l) \cdot \exp\left(-\frac{(i-k)^2 + (j-l)^2}{2\sigma_s^2}\right) \cdot \exp\left(-\frac{(I(i, j) - I(k, l))^2}{2\sigma_r^2}\right)
   $$
   where:
   - \( W_p \) is the normalization factor.
   - \( \sigma_s \) is the spatial standard deviation.
   - \( \sigma_r \) is the range standard deviation.

## Pros and Cons
- **Pros**:
  - Preserves edges while reducing noise.
  - Effective for images with high contrast edges.
- **Cons**:
  - Computationally intensive.
  - Requires careful tuning of parameters.

## When to Use
- Use when you need to reduce noise while preserving edges in images.

## Sample Code Implementation

Here's a simple implementation in Python using OpenCV:

```python
import cv2
import numpy as np
from matplotlib import pyplot as plt

# Load the image
img = cv2.imread('image.jpg')

# Apply bilateral filter
bilateral_filtered_img = cv2.bilateralFilter(img, 15, 75, 75)

# Display the results
plt.subplot(121), plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB)), plt.title('Original Image')
plt.subplot(122), plt.imshow(cv2.cvtColor(bilateral_filtered_img, cv2.COLOR_BGR2RGB)), plt.title('Bilateral Filtered Image')
plt.show()
