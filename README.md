# Ai-enabled-car-parking-using-opencv
OpenCV is an extensive open source library (available in python, Java, and C++) that's used for image analysis and is pretty neat.

The lofty goal for my OpenCV experiment was to take any static image or video of a parking lot and be able to automatically detect whenever a parking space was available or occupied.
What I was able accomplish was to detect how many spots were available in a parking lot, with just a bit of upfront work by the user.

I'll start with an overview, then talk about my process, and end with some ideas for future work.
Overview

Applying gray filter to original image

gray=cv.cvtColor(img,cv.COLOR_BGR2GRAY)
![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/f091c959-b238-4e98-8916-957cbf029da9)


![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/e7e1e637-7ff8-45fe-b877-6cf477dca426)
![image](https://github.com/Vamsi59/Ai-enabled-car-parking-using-opencv/assets/94848154/be51b85f-78fc-4202-a107-116b8333f728)
