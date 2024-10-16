# EDGE LINKING HOUGH TRANSFORM

## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:

Anaconda - Python 3.7

## Algorithm:

### Step1:
Read the image

### Step2:
Convert the input image to gray to get more details

### Step3:
Apply any smoothing filter, here we apply Gaussian blur

### Step4:
Apply an edge detector

### Step5:
Apply hough transform and show the detected edge on the original image


## Program:

```
Developed By : Dhiyaneshwar P
Register Number : 212222110009
```
```Python

# Read image and convert it to grayscale image
import cv2
import numpy as np
r=cv2.imread('bird.jpg',-1)
gray=cv2.cvtColor(r,cv2.COLOR_BGR2GRAY)
img = cv2.GaussianBlur(gray,(3,3),0)
cv2.imshow('origianl',r)
cv2.waitKey(0)
cv2.destroyAllWindows()
cv2.imshow('gray',gray)
cv2.waitKey(0)
cv2.destroyAllWindows()


# Find the edges in the image using canny detector and display
canny_edges = cv2.Canny(img, 50, 120)
cv2.imshow('canny',canny_edges)
cv2.waitKey(0)
cv2.destroyAllWindows()


# Detect points that form a line using HoughLinesP
lines =cv2.HoughLinesP(canny_edges, 1, np.pi/180,threshold = 15, minLineLength =5 ,
maxLineGap = 7)



# Draw lines on the image
for line in lines:
 x1,y1,x2,y2 = line[0]
 cv2.line(r, (x1,y1),(x2,y2),(255,0,0),3)



# Display the result
cv2.imshow('hough_detected',r)
cv2.waitKey(0)
cv2.destroyAllWindows()



```
## Output

### Input image and grayscale image

![image](https://github.com/user-attachments/assets/30b69b64-3752-4e6b-86f2-01d77677b6a3)

![image](https://github.com/user-attachments/assets/055c39a4-70ff-44c4-ae71-b2fe1f578f85)

### Canny Edge detector output

![image](https://github.com/user-attachments/assets/e6a7f8db-0c7b-4edb-ad85-48223750945c)

### Display the result of the Hough transform

![image](https://github.com/user-attachments/assets/edc90b7a-3180-4bad-9dcd-c576da8da5bb)

## Result:
Thus the program is written with Python and OpenCV to detect lines using Hough transform. 
