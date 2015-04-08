Volume Adjustment Effects
=========================

Audacity applies fade effects by multiplication of the waveforms. Fade in/out just use a range of values from 0 to 1, which can be spread out exponentially, linearly, or logarithmically depending on where the highest slope is desired. On it’s own, fade is often used to remove clicks from the beginning of tracks as they transition from silence.
Audacity can also apply an equal-power fade, or crossfade, on multiple tracks to transition between them while keeping the power the same, or in most cases, slightly increasing it at the middle to leave room for volume dips in the center of the fade.

Amplification and normalization are very similar processes, they both add gain to the track, however normalization differs in a few ways:  
- Corrects DC offset
- Prevents clipping by disallowing normalization beyond 0 dB
- Can be applied on multiple tracks or channels to remove level difference
Because normalization requests a set dB level for peak amplitude adjustment, it works well on multiple tracks that have different volumes, on the other hand, amplification merely adds a certain amount of gain so the difference will be kept intact. In some scenarios this is desired.

Compression is often confused with normalization because what it does can also be described by saying that the volume levels across the track are normalized, however, compression acts by first reducing the gain of samples above a certain threshold, then amplifying the entire track to leave the high gain samples untouched, but the lower power segments increased. 

