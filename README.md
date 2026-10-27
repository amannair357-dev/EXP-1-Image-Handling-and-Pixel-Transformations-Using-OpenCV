# EXP-1-Image-Handling-and-Pixel-Transformations-Using-OpenCV

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** Aman Nair
- **Register Number:** 212225240008

  ### Ex. No. 01
  
~~~python
import cv2
import numpy as np
import matplotlib.pyplot as plt

### 1. Read grayscale image
img = cv2.imread('img.jpg', 0)

### 2. Print width, height and channel
print("Width:", img.shape[1])
print("Height:", img.shape[0])
print("Channel: 1")

### 3. Display grayscale image
plt.imshow(img, cmap='gray')
plt.show()

### 4. Save as PNG
cv2.imwrite('img.jpg', img)

### 5. Read saved image as color
img_color = cv2.cvtColor(cv2.imread('img.jpg'), cv2.COLOR_BGR2RGB)

### 6. Display color image and print dimensions
print("Width, Height, Channel:", img_color.shape[1], img_color.shape[0], img_color.shape[2])
plt.imshow(img_color)
plt.show()

### 7. Crop the eagle (adjust coordinates if needed)
cropped = img_color[100:400, 100:400]

### 8. Resize by 2x
resized = cv2.resize(cropped, None, fx=2, fy=2)

### 9. Flip horizontally
flipped = cv2.flip(resized, 1)
plt.imshow(flipped)
plt.show()

### 10. Read image
img = cv2.imread('img.jpg')

### 11. Add text
text = 'Animals'
font = cv2.FONT_HERSHEY_PLAIN
h, w = img.shape[:2]

cv2.putText(img, text, (50, h-20), font, 1.5, (255,255,255), 2)

### 12. Draw magenta rectangle (adjust coordinates)
cv2.rectangle(img, (200, 50), (500, 500), (255, 0, 255), 2)

### 13. Display final image
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.show()

### 14. Read image
img = cv2.imread('img.jpg')

### 15. Create matrix of ones
matrix = np.ones(img.shape, dtype=np.uint8) * 50

### 16. Adjust brightness
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)

### 17. Display original, darker and brighter
plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original')

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title('Darker')

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title('Brighter')

plt.show()

# 18. Modify contrast
matrix1 = np.ones(img.shape, dtype=np.float64) * 0.9
matrix2 = np.ones(img.shape, dtype=np.float64) * 1.2

img_lower = cv2.multiply(img, matrix1, dtype=cv2.CV_8U)
img_higher = cv2.multiply(img, matrix2, dtype=cv2.CV_8U)

# 19. Display images
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1, 3, 2)
plt.imshow(cv2.cvtColor(img_lower, cv2.COLOR_BGR2RGB))
plt.title("Lower Contrast")

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(img_higher, cv2.COLOR_BGR2RGB))
plt.title("Higher Contrast")

plt.show()

### Read image
img = cv2.imread('img.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

### 20. Split B, G, R channels
b, g, r = cv2.split(img)

plt.figure(figsize=(10,4))
plt.subplot(1,3,1)
plt.imshow(b, cmap='gray')
plt.title('Blue')

plt.subplot(1,3,2)
plt.imshow(g, cmap='gray')
plt.title('Green')

plt.subplot(1,3,3)
plt.imshow(r, cmap='gray')
plt.title('Red')
plt.show()

### 21. Merge R, G, B and display
merged = cv2.merge([r, g, b])
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.title('Merged Image')
plt.show()

### 22. Split H, S, V channels
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)

plt.figure(figsize=(10,4))
plt.subplot(1,3,1)
plt.imshow(h, cmap='gray')
plt.title('Hue')

plt.subplot(1,3,2)
plt.imshow(s, cmap='gray')
plt.title('Saturation')

plt.subplot(1,3,3)
plt.imshow(v, cmap='gray')
plt.title('Value')
plt.show()

### 23. Merge H, S, V and display with original
merged_hsv = cv2.merge([h, s, v])
merged_color = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)

plt.figure(figsize=(8,4))
plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title('Original')

plt.subplot(1,2,2)
plt.imshow(merged_color)
plt.title('Merged HSV')

plt.show()
~~~

## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.

<img width="855" height="556" alt="image" src="https://github.com/user-attachments/assets/bf1d0cef-5f98-42aa-bcb2-412219008853" />
<img width="1546" height="590" alt="image" src="https://github.com/user-attachments/assets/6b1235bd-5ffe-4006-9c11-f5df1ab1f8af" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

