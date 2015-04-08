Image Processing
================

The image processing part of the conductifier is concerned with locating the conducting target indicator within a frame of the input video. This step begins by establishing a connection with the first available webcam on the host system. This is done through OpenCV, the open computer vision library. Once connected, frames are requested from the webcam as fast as possible.

Once a frame is read, it is converted to 8-bit grayscale. This reduces the size of the image, and therefore accelerates all the following steps. Next, the conductifier runs ORB on the frame. ORB is a feature detection algorithm that, when given an image, locates the keypoints and features within the image. These represent things like sharp edges or noticeable corners, and are akin to a fingerprint of the image. They are then searched for a copy of a the keypoints of the target indicator and a homography matrix, representing the transform of the keypoints from the targeting indicator, is found. The homography matrix is then applied to the four corner points of the targeting indicator. The center of the transformed square is then recorded as the location of the targeting indicator for the frame, provided is does not differ from the previous location by more than half the frames distance (to avoid erroneous matches). This value is sent to the signal smoothing process to be adjusted before being applied to the audio.