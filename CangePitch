Change Pitch
------------

The change pitch feature of Audacity enables the pitch of an audio file to be changed by allowing the user to 
either enter a semitone change, a percent change in frequency, or a desired key. The effect starts by deducing the
from frequency:  
The general idea of the DeduceFrequencies() method is as follows:  
1.Generate a window size based on the sample rate
2.Calculate the number of windows requred to fill about 0.2 seconds
3.Sum the results of a fast fourier transform performed on each window
4.Use the peak value of the fast fourier transform along with the windowsize and the sample rate to calculate the freqency 
  
The FFT function used is based on an implementation by Don Cross available here: http://www.intersrv.com/~dcross/fft.html
and has been improved with caching techniques and elimination of type conversions.
This method is also not guarenteed to produce the correct frequency, some lacking parts of the implementation include:  
1.No low-passing is done  [2]
  This can cause noise or higher frequencies to mask the dominant frequency, or more likely to be masked by harmonics that
  appear more powerful than the fundemental frequencies.
2.No special window function is used  [2]
  Typically either a Hamming or Hann window function is used when creating windows, the problem with taking windows
  as just a function of the sampling rate is that it is possible for artifacts to be created at the edges of the windows
  due to lack of consideration at where the start and end points are located, these artifacts can also mask the dominant
  frequency
However these issues only have an effect on audio data in rare cases.

Once the from frequency is deduced, the MIDI note is calculated according to the A440 pitch standard, and the user is 
prompted to enter their desired pitch shift and this value is input into the SoundTouch library in semitone changes.

The SoundTouch library then uses a combination of time-stretching and sample rate transposing to shift the pitch
the desired amount, see details about the algorithms sound touch uses in the SoundTouch file [[[to be done!]]]



[2]http://blog.bjornroche.com/2012/07/frequency-detection-using-fft-aka-pitch.html
