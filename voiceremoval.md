Voice Removal
=============

Vocal removal is a Nyquist (LISP derivative) effect. It requires a stereo track with center panned vocals, which is a standard location for vocals in most modern mixed music. The effect takes three forms: Simple, Remove, or Retain. In simple mode, it considers audio across the entire frequency spectrum as vocals. Remove mode considers all audio outside the specified frequency band to be vocals, and Retain mode considers all audio within the specified band to be vocals. Once mode is selected, the left track of the stereo input audio is inverted and added to the right track, the frequencies that were not considered vocals are pulled out of the source audio with low/high pass filters and added to the result. The resulting audio will not contain any signals that were mixed to the center and within the frequencies chosen to be vocals.

This procedure is weak in several ways. First, it does not perform well on compressed audio. A sound may be deleted from one side of the stereo track but not the other due to frequency masking or temporal masking. This would then garble the sound post removal, as the vocals are not present on both sides at precisely that instant. The second major weakness is the presence of other centrally mixed signals, typically drums. While selecting frequencies that are considered vocals mitigates this somewhat, it does not address scenarios where other centrally mixed audio overlaps the vocals. A more clever deduction of vocal frequencies would improve the accuracy of this tool.
