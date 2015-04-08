Proposal – Project Panic Beats
==============================
Noah Spriggs, V00772732  
Murray Dunne, V00773350


Project Statement
-----------------
Audacity, an audio manipulation tool, was initially developed by Dominic Mazzoni and Roger Dannenberg in 1999. It became open source in 2000. Hosted on SourceForge, Audacity is maintained by a passionate group of open source contributors. However there are still many features desired by the user base.
	We propose an analysis of the audio capturing and modifying techniques that are included in the recording software Audacity. We will investigate tools and algorithms Audacity uses for recording and editing waveform audio.  
	
Approach & Deliverables
-----------------------
We will produce a comprehensive list of the audio manipulation tools and their respective algorithms used in Audacity, including a discussion of the merits of the chosen algorithm and the benefits and disadvantages of possible alternatives.
	We will also investigate the recording infrastructure of the program, including the device types supported, the API used, and the benefits and drawback of each. Time and infrastructure permitting we will add a tool to Audacity that provides a desired feature not present in the current version of Audacity.  
Schedule
--------
Week Of
Feb 9th	
-	Download and examine the source code of Audacity. 
-	Become comfortable with using Audacity to record and edit audio.  

Feb 23rd	
-	Compile a list of the audio manipulation tools used in Audacity.  
	https://github.com/noahspriggs/panicbeats/blob/master/toollist.md
-	For each tool, determine the relevant algorithm used.  
  -	[Undo-redo](https://github.com/noahspriggs/panicbeats/blob/master/undoredo.md)
  -	[Change Pitch](https://github.com/noahspriggs/panicbeats/blob/master/changepitch.md)
  -	[Reverb](https://github.com/noahspriggs/panicbeats/blob/master/reverb.md)
  -	[Voice Removal](https://github.com/noahspriggs/panicbeats/blob/master/voiceremoval.md)
  -	[Noise Removal](https://github.com/noahspriggs/panicbeats/blob/master/noiseremoval.md)
  -	[Volume Adjustment](https://github.com/noahspriggs/panicbeats/blob/master/volumeadjustmenteffects.md)


Mar 9th	
- Find a list of supported recording devices by type or API compatibility.
-	Analyze the tool algorithms for benefits and disadvantages in possible alternatives.  
  -	[Undo-redo](https://github.com/noahspriggs/panicbeats/blob/master/undoredo.md)
  -	[Change Pitch](https://github.com/noahspriggs/panicbeats/blob/master/changepitch.md)
  -	[Reverb](https://github.com/noahspriggs/panicbeats/blob/master/reverb.md)
  -	[Voice Removal](https://github.com/noahspriggs/panicbeats/blob/master/voiceremoval.md)
  -	[Noise Removal](https://github.com/noahspriggs/panicbeats/blob/master/noiseremoval.md)
  -	[Volume Adjustment](https://github.com/noahspriggs/panicbeats/blob/master/volumeadjustmenteffects.md)

Mar 23rd
- Determine the benefits and drawbacks of the various device types.
-	Time/infrastructure permitting: create and integrate a new tool into Audacity.  
  -	[Structure](https://github.com/noahspriggs/panicbeats/blob/master/pluginstructure.md)
  -	[Image Processing](https://github.com/noahspriggs/panicbeats/blob/master/imageprocessing.md)
  -	[Signal Smoothing](https://github.com/noahspriggs/panicbeats/blob/master/signalsmoothing.md)

URL
---
https://github.com/noahspriggs/panicbeats 
