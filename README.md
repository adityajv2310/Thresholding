# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm
### Step 1:
Load the necessary packages.

### Step 2:
Read the Image and convert to grayscale.

### Step 3:
Use Global thresholding to segment the image.

### Step 4:
Use Adaptive thresholding to segment the image.

### Step 5:
Use Otsu's method to segment the image.

### Step 6:
Display the results.

## Program

```python
# Load the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale
image=cv2.imread("leaf.jpg",1)
image=cv2.cvtColor(image,cv2.COLOR_BGR2RGB)
image_gray=cv2.imread("leaf.jpg",0)

# Use Global thresholding to segment the image
ret,thresh_img1=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY)
ret,thresh_img2=cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY_INV)
ret,thresh_img3=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO)
ret,thresh_img4=cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO_INV)
ret,thresh_img5=cv2.threshold(image_gray,100,255,cv2.THRESH_TRUNC)

# Use Adaptive thresholding to segment the image
thresh_img7=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
thresh_img8=cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)

# Use Otsu's method to segment the image 
ret,thresh_img6=cv2.threshold(image_gray,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results
titles=["Gray Image","Threshold Image (Binary)","Threshold Image (Binary Inverse)","Threshold Image (To Zero)"
       ,"Threshold Image (To Zero-Inverse)","Threshold Image (Truncate)","Otsu","Adaptive Threshold (Mean)","Adaptive Threshold (Gaussian)"]
images=[image_gray,thresh_img1,thresh_img2,thresh_img3,thresh_img4,thresh_img5,thresh_img6,thresh_img7,thresh_img8]
for i in range(0,9):
    plt.figure(figsize=(10,10))
    plt.subplot(1,2,1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1,2,2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()

```
## Output

### Original Image
![image](https://user-images.githubusercontent.com/75235386/170621764-443cb690-191d-44cc-817e-89123f3dd0ac.png)

### Global Thresholding
![image](https://user-images.githubusercontent.com/75235386/170621792-a31af4f9-95bd-4c13-883d-7da9ea0acd0e.png)
![image](https://user-images.githubusercontent.com/75235386/170621844-73848c8e-8c1f-4b47-a61b-8a1826ef0361.png)
![image](https://user-images.githubusercontent.com/75235386/170621871-d616433a-160f-4ab6-ac0e-2fd3d2fbcb4e.png)
![image](https://user-images.githubusercontent.com/75235386/170621897-990dc813-4b6b-45ea-83ad-87d6a6af57da.png)
![image](https://user-images.githubusercontent.com/75235386/170621951-e65c8b62-d931-44ee-83d2-bf65f9a75547.png)


### Adaptive Thresholding
![image](https://user-images.githubusercontent.com/75235386/170622068-2ff7a357-feb8-46fd-8d66-d99b5cd1f74c.png)
![image](https://user-images.githubusercontent.com/75235386/170622111-dba1c218-eaec-458e-b450-2ed9da8f543a.png)


### Optimum Global Thesholding using Otsu's Method
![image](https://user-images.githubusercontent.com/75235386/170621999-dfbb8ea4-30db-4a13-a326-c1f8185847de.png)



## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

