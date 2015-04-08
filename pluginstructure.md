Plugin Structure
=====================

The conductifier plugin for Audacity was built to familiarise ourselves with Audacity’s internal structure and plugin interface. It was also built to tie in more elements of the course, such as video and imaging. This portion of the paper will outline the functionality of the conductifier plugin, broadly describe how it works, and provide details on specific portions of functionality.

The conductifier is a LADSPA plugin and is composed of two parts: the shared library and the conductifier application (herein called the conductifier). The shared library implements the LADSPA interface. When started from Audacity, the shared library connects to the conductifier and forwards the audio data. The conductifier processes the data, then returns it to the shared library, which passes it back to audacity.

The conductifier is separated into three distinct parts: image processing, signal smoothing, and audio acceleration. For a demonstration of the conductifier in action, see: https://www.youtube.com/watch?v=orgqY5Aaml8.
