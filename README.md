# Ai-enabled-car-parking-using-opencv
OpenCV is an extensive open source library (available in python, Java, and C++) that's used for image analysis and is pretty neat.

The lofty goal for my OpenCV experiment was to take any static image or video of a parking lot and be able to automatically detect whenever a parking space was available or occupied.
What I was able accomplish was to detect how many spots were available in a parking lot, with just a bit of upfront work by the user.

I'll start with an overview, then talk about my process, and end with some ideas for future work.

Original Image:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/1e0ea015-4377-494a-9ed5-710f8ddfd5d6)

Applying gray filter to original image:

gray=cv.cvtColor(img,cv.COLOR_BGR2GRAY)

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/f091c959-b238-4e98-8916-957cbf029da9)

Applying Gaussian blur to remove even more unnecessary noise:

blur_gray = cv2.GaussianBlur(src=gray, ksize=(5, 5), sigmaX=0)

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/6d69ec0d-f256-4fbe-9aa3-ccc82bf2bea5)

Applying image Tresholding to GaussianBlur image:

imgThreshold = cv2.adaptiveThreshold(imgBlur, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY_INV,25, 16)

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/5e89a6f0-e758-4e2e-a245-e8874191ddcc)

Applying image median to image Tresholding:

imgMedian = cv2.medianBlur(imgThreshold, 5)

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/3075f971-9de0-4878-842a-398a8af07420)

Applying Dilation to image median:

kernel = np.ones((3, 3), np.uint8)
imgDilate = cv2.dilate(imgMedian, kernel, iterations=1)
        
![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/2065459c-79c7-43e0-9718-53823a672d2e)

Which gave me more lines, but I still had to figure out which lines were part of the parking space and which weren't. Then, I would also need to detect when a car moved from a spot.Which would also call for a mask to cover unimportant information (trees, light posts, etc.)

Flask Running on server:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/e7e1e637-7ff8-45fe-b877-6cf477dca426)

Home Page:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/38e25eb0-5700-4e8f-a007-34ee32ad786c)

About us page:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/3e0b6c1d-12db-45c2-9dc3-1ae5b8f4ddfc)

Registration Page:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/983d462a-7e1e-46d2-bac5-a0a866b77bf0)

Login Page:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/4b330cb4-3433-49fa-9f16-a04f69130f85)

After Login:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/a30de279-d8b6-4557-9b1c-23bdd5cebf8b)

Output page:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/be51b85f-78fc-4202-a107-116b8333f728)

Contact Page:

![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/5d8e9924-e967-4576-8af0-a42c94c03343)

