Introduction
############

Background
==========

Konfyt is a digital keyboard workstation for Linux. It allows you to instantly switch
between patches for live keyboard playing. Each patch can contain multiple layers of
soundfont (SF2 or SFZ) instruments, as well as audio input ports from, and MIDI output
ports to other apps or hardware. Konfyt also has a searchable library which scans your
filesystem for instruments and lets you easily browse and search soundfont contents.

Konfyt originally started out in 2014 as a library for soundfonts for quick viewing of
contents since the existing methods was frustrating. From there it got SFZ support and
eventually grew into a fully fledged live keyboard playing tool ("workstation").

Concept
=======

Konfyt is a stand-alone application that uses JACK for audio and MIDI input and output.
Konfyt hosts SF2 and SFZ instruments and does audio and MIDI routing. Additional tasks such
as effects and synth plugins must be done outside Konfyt by other software. Konfyt is
designed to easily integrate into the Linux pro audio world. It allows you to use all
your other JACK aware software while filling the gap of routing audio
and MIDI in a very user friendly way with instant patch switching and other useful
features geared towards live keyboard playing.

Features
========

* Scan filesystem for soundfonts and SFZs and organize it into a tree view for easy navigation.

* List soundfont contents (programs) by simply selecting a soundfont in the library.

* Search library for SFZs and soundfonts, including soundfont programs.

* Uninterrupted patch switching - when holding notes or sustain while switching patches, sound keeps on playing until release.

* Audio input ports, which can be inserted into patches as layers, allowing audio to be received from other applications or from system input.

* MIDI output ports, which can be inserted into patches as layers, allowing MIDI output to other applications or to hardware.

* Audio output busses, allowing the output of SFZ, soundfont and audio-in layers to be sent to different destinations.

* Port connections to other JACK clients are automatically persisted.

* Per layer MIDI filter including key zone, transpose, velocity filtering and MIDI CC filtering.

* Assign MIDI triggers to actions such as switching patches and modifying layer volume, mute and solo.

* MIDI events (including Sysex messages) can automatically be sent to an output port when a patch is activated - useful to change programs and modes on an external synthesizer.

* Per project external application launcher. Add commands and arguments for all external applications associated with your project to a list to easily launch them. Application files can be saved to the project directory and referenced relative to the directory, allowing for everything contained in a single directory and remaining in tact when the directory is moved.

* Filesystem browser to quickly load SFZs and soundfonts from directories not in the library.

* Live mode in which some actions can be controlled with the computer keyboard.

* Panic button which, when activated, mutes all sounds, stops all MIDI and emits MIDI all-notes-off messages as well as pitchbend zero and sustain pedal zero.

* Scalable GUI which fits comfortably on a 1366x768 laptop display.





