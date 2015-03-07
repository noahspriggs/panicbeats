Reverb

Audacity produces the reverberation effect using a digital convolution. The user may specify the characteristics of the room in which the reverberation is simulated, or they can select for a set of pre-designed rooms. These parameters are then used to generate the impulse response function of the room, which represents the waveform received by the listener in the room when a mathematically ideal impulse is played [1]. The audio signal is convoluted with this waveform after a high and low pass filter are applied. Audacity does this discrete convolution manually on the CPU.  This is a destructive operation, the original audio is lost except for its presence on the undo stack.

Considerations:
	1) Simulating the Impulse Response function is inferior to using a sampled response from an actual room.
	2) The convolution can be done more efficiently by modern graphics cards than CPUs.

1) While it is impossible to produce a mathematically ideal impulse in reality, approximations have been used and the response recorded. Many of these are available publicly [2]. Because these represent the actual features of real rooms, they produce more realistic results when used in convolutions. Is a physical audio pipeline, a series of metal rods suspended on springs is used to produce true reverberation. 
While Audacity could use sampled room impulse response functions, most software also uses mathematical versions because they allow for more options than sampling a physical room. Therefore, there is no clear cut resolution to this problem, and Audacity's decision to use the mathematical version is perfectly understandable.

2) The GPU in modern computers is far more capable then the CPU when it comes to large mathematical operations with little branching. Convolutions have no branching, so the GPU can leverage its massive parallelization abilities to drastically increase the speed at which this operation is done.
The cross platform OpenGL graphics library provides access to the GPU across all common consumer operating systems. It would be relativity simple for audacity to use OpenGL to do mathematical operations on the GPU, as wxWidgets (the user interface framework used by Audacity) provides support for acquiring OpenGL resources. This may take some investment of developer effort, but the results would be significant on longer audio files.

In conclusion, Audacity uses simulated impulse response functions convoluted with the original signal to produce the reverberated sound. Using a simulated function, while not as accurate as a sampled function, offers more choice of room characteristics to the user. Using the GPU to do the convolution itself would result in much faster results, but may take significant developer effort.

[1] F. Adriaensen. (2006). Acoustical Impulse Response Measurement with ALIKI [Online]. Available: http://lac.zkm.de/2006/papers/lac2006_fons_adriaensen_01.pdf
[2] M. Schafer. (2012). Aachen Impulse Response Database [Online]. Available: http://www.ind.rwth-aachen.de/en/research/tools-downloads/aachen-impulse-response-database/
