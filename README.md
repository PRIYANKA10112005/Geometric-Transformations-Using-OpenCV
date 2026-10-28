# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program
```py
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('baseball.jpg.jpeg')
filename = "baseball.jpg.jpeg"
print("File exists:", os.path.exists(filename))
image = cv2.imread(filename)
print("Image loaded:", image is not None)
print("Image shape:", image.shape)
plt.imshow(image[:,:,::-1])
plt.title('Original Image')
plt.show()
tx, ty = 100, 200
M_translation = np.float32([[1, 0, tx],[0, 1, ty]])
translated_image = cv2.warpAffine(image, M_translation,(image.shape[1], image.shape[0]))
plt.figure(figsize=(10,5))
plt.subplot(1,2,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(translated_image[:,:,::-1])
plt.title("Translated Image")
plt.axis("off")
plt.show()
downscaled_image = cv2.resize(image, None,fx=0.25,fy=0.25,interpolation=cv2.INTER_LINEAR)
upscaled_image = cv2.resize(image, None,fx=3,fy=3,interpolation=cv2.INTER_LINEAR)
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled_image[:,:,::-1])
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled_image[:,:,::-1])
plt.title("Upscaled Image")
plt.axis("off")

plt.show()

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled_image[:,:,::-1])
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled_image[:,:,::-1])
plt.title("Upscaled Image")
plt.axis("off")

plt.show()
vertical_matrix = np.float32([[1,0,0],[0.5,1,0]])
vertical_shear = cv2.warpAffine(image,vertical_matrix,(image.shape[1], image.shape[0]))
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal_shear[:,:,::-1])
plt.title("Horizontal Shear")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical_shear[:,:,::-1])
plt.title("Vertical Shear")
plt.axis("off")

plt.show()
horizontal = cv2.flip(image,1)
vertical = cv2.flip(image,0)
both = cv2.flip(image,-1)
plt.figure(figsize=(10,10))

plt.subplot(2,2,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.imshow(horizontal[:,:,::-1])
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2,2,3)
plt.imshow(vertical[:,:,::-1])
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2,2,4)
plt.imshow(both[:,:,::-1])
plt.title("Both Axes Reflection")
plt.axis("off")

plt.show()
(height, width) = image.shape[:2]

center = (width//2, height//2)
matrix45 = cv2.getRotationMatrix2D(center,45,1)
rotate45 = cv2.warpAffine(image,matrix45,(width,height))
matrix90 = cv2.getRotationMatrix2D(center,90,1)
rotate90 = cv2.warpAffine(image,matrix90,(width,height))
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotate45[:,:,::-1])
plt.title("45 Degree Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotate90[:,:,::-1])
plt.title("90 Degree Rotation")
plt.axis("off")

plt.show()
```


### Developed By:
**Name:** PRIYANKA P

### Register No: 212224230212

---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed
<img width="1016" height="338" alt="image" src="https://github.com/user-attachments/assets/1378c416-4491-426e-8d87-5b2637056318" />


### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed
<img width="1357" height="297" alt="image" src="https://github.com/user-attachments/assets/cc4029fb-2a3e-4b10-b8bb-ec9f80253702" />


### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed
<img width="1350" height="296" alt="image" src="https://github.com/user-attachments/assets/d8b09ad3-cb23-461a-b605-b64b220d4cc3" />


### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed
<img width="990" height="856" alt="image" src="https://github.com/user-attachments/assets/73ae08d2-dde1-49da-9459-d3a02d503e09" />


### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed
<img width="1352" height="301" alt="image" src="https://github.com/user-attachments/assets/1479bd40-eda4-4298-a636-2e5bcc025275" />


---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
