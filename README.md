# EXP-4-Geometric-Transformations-Using-OpenCV
## Aim
To write a Python program using OpenCV to perform various geometric transformations on an image.
The program performs the following operations:

- Image Translation
- Image Scaling (Resizing)
- Image Shearing
- Image Reflection (Flipping)
- Image Rotation

## Software Used
- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm
### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image
- Move the image 50 pixels to the right and 80 pixels down
- Apply transformation using cv2.warpAffine()
- Display original and translated images

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)
- Resize the image to 2× (upscale)
- Use cv2.resize()
- Display original, downscaled, and upscaled images

### Step 5: Image Shearing
- Create transformation matrices for:
       - Horizontal shearing
       - Vertical shearing
- Apply transformations using cv2.warpAffine()
- Display original and sheared images

### Step 6: Image Reflection
- Perform flipping using cv2.flip():
       - Horizontal reflection
       - Vertical reflection
       - Both axes
- Display all reflected images

### Step 7: Image Rotation
- Create rotation matrices for:
       - 45° rotation
       - 90° rotation
- Use cv2.getRotationMatrix2D() and cv2.warpAffine()
- Display original and rotated images

## Program
### Developed By:
#### Name: SAADHANA A
### Register No: 212225240126

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('pic .jpg')
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB)) 
plt.axis('off')
tx, ty = 100, 50 
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB)) 
plt.title("Translated Image")  
plt.axis('off')
fx, fy = 5.0, 2.0 
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  
plt.title("Sheared Image") 
plt.axis('off')
reflected_image = cv2.flip(image, 2)
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))
plt.title("Reflected Image") 
plt.axis('off')
(height, width) = image.shape[:2]  
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2) 
M_rotation = cv2.getRotationMatrix2D(center, angle, 1) 
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  
plt.title("Rotated Image") 
plt.axis('off')
x, y, w, h = 100, 100, 200, 150
cropped_image = image[y:y+h, x:x+w]
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```

## Output
### Image Translation
- Original image is displayed
- Translated image (shifted right and down) is displayed

  <img width="471" height="256" alt="Screenshot 2026-08-06 135154" src="https://github.com/user-attachments/assets/884696b3-2665-474d-acad-a2f1280bb768" />

### Image Scaling
- Original image is displayed
- Downscaled image (0.5×) is displayed
- Upscaled image (2×) is displayed

  <img width="467" height="266" alt="Screenshot 2026-08-06 135204" src="https://github.com/user-attachments/assets/1dd4141f-da8e-4e25-9e4e-2e10cdb98fa5" />

  <img width="490" height="151" alt="Screenshot 2026-08-06 135223" src="https://github.com/user-attachments/assets/fc83413f-ddba-4457-b76c-a6f4ce754b84" />

### Image Shearing
- Original image is displayed
- Horizontally sheared image is displayed
- Vertically sheared image is displayed

  <img width="487" height="269" alt="Screenshot 2026-08-06 135241" src="https://github.com/user-attachments/assets/14ff3a25-9302-46dd-8bfc-fc12f306f7c4" />

### Image Reflection
- Original image is displayed
- Horizontally flipped image is displayed
- Vertically flipped image is displayed
- Both-axis flipped image is displayed

  <img width="466" height="258" alt="Screenshot 2026-08-06 135252" src="https://github.com/user-attachments/assets/ec7abde7-02ee-44ef-b3ea-b347cf742f9e" />

### Image Rotation
- Original image is displayed
- 45° rotated image is displayed

   <img width="457" height="260" alt="Screenshot 2026-08-06 135300" src="https://github.com/user-attachments/assets/490f1d5f-14f8-4486-b154-bafbc7b1cb0f" />
  
- 90° rotated image is displayed

   <img width="462" height="354" alt="Screenshot 2026-08-06 135311" src="https://github.com/user-attachments/assets/fe10405c-4d61-4135-87c2-49e77250d8e8" />

- Use cv2.getRotationMatrix2D() and cv2.warpAffine()
- Display original and rotated images

  

### Result
Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
