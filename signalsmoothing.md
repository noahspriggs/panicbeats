Signal Smoothing
================

The signal smoothing step takes the location of the targeting indicator within a frame and calculates the velocity that the user is conducting at. Figure 4 shows this process in action.

![figure 4](http://i.imgur.com/YRd8via.png)

First the x and y positions ((a) and (b) in Figure 4 respectively) are converted to a continuous signal using linear interpolation. This is required for all the following techniques, which all operator on continuous signals. Next an exponentially weighted moving average is taken of the x and y positions ((c) and (d) respectively) with each hundredth of a second weighted as 3% of the next signal value. This removes most of the jitter from variance in the image processing step and the users movement. Part (e) shows the current location of the conducting target within the frame after smoothing is applied. The current two-dimensional velocity of the conducting target within the frame is then established (considering the center of the frame to be the origin and the frame to be two units wide) (f). This is then smoothed by exponentially weighted moving average again (g). Next the smoothed velocity is clamped to steps of size 1 (0.0, 1.0, 2.0) and the result is moving averaged again (h). This signal is clamped again to [0.5, 2.0], as both extremes of the range are significantly distorted and confuse users regarding their position within the audio. This final signal determines the velocity to accelerate the audio.

