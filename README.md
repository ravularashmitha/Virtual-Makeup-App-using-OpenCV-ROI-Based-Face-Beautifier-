
# ROI-Based Virtual Makeup and Face Beautifier using OpenCV

## Objective

This project demonstrates how image processing and computer vision techniques can be used to apply virtual makeup effects such as skin smoothing, lip tinting, and filters on a manually selected Region of Interest (ROI) — without using face detection.

## Technologies Used

* Python
* OpenCV
* NumPy
* Jupyter Notebook

## Key Features

* Manual ROI selection for targeted editing
* Skin smoothing using Gaussian or median blur
* Lip tint and blush coloring using HSV masking
* Morphological transformations for mask refinement
* Bitwise operations for seamless blending
* Affine transformations for adding filters or stickers
* Interactive trackbars for adjusting color and blur intensity

## Makeup Styles

| Style        | Description                                           |
| ------------ | ----------------------------------------------------- |
| Natural Look | Light blur and soft tint                              |
| Glam Look    | Stronger brightness and color intensity               |
| Funny Look   | Stickers and geometric filters using affine transform |

## Concepts Demonstrated

* ROI extraction
* Gaussian and median blurring
* HSV color space masking
* Morphological transformations (erosion and dilation)
* Bitwise masking and blending
* Affine transformations

## Output

Displays both the original and processed images side by side.
Final image can be saved using `cv2.imwrite()


## Example Code Snippet

```python
# Load and display image
img = cv2.imread('face.jpg')
r = cv2.selectROI("Select Face", img)
roi = img[int(r[1]):int(r[1]+r[3]), int(r[0]):int(r[0]+r[2])]

# Apply smoothing
smooth_roi = cv2.GaussianBlur(roi, (15, 15), 0)

# Convert to HSV and create mask
hsv = cv2.cvtColor(roi, cv2.COLOR_BGR2HSV)
lower = np.array([160, 80, 80])
upper = np.array([180, 255, 255])
mask = cv2.inRange(hsv, lower, upper)

# Merge processed ROI
img[int(r[1]):int(r[1]+r[3]), int(r[0]):int(r[0]+r[2])] = smooth_roi


Here is the reference video (what is the project flow):
https://drive.google.com/file/d/1y39riBup-1i6EqKv0RokzfnSiiv9Lgl2/view?usp=drivesdk
