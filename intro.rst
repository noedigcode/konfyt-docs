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



Settings
========

It is a good idea to fill in all the options in the settings screen.

File Manager
------------

The file manager entry is optional and is provided in case your default file manager doesn't play along well. You can test it by right-clicking on one of the library items and clicking *Open in File Manager*. If you receive an error message from your file manager, specify your preferred file manager in settings (e.g. either dolphin, nautilus, thunar, pcmanfm, etc.).

Projects Directory
------------------

This is the default directory for projects. This directory is scanned at startup and all the projects are listed in the projects Open menu for easy access. When saving a project you can seamlessly save it in this directory by accepting the proposed path (or choose No to select a different path).

Scanning
--------

The *Apply and Rescan* button clears the database and scans the specified directories and subdirectories for SFZs, GIGs, soundfonts (sf2) and patches. This may take a while, especially with big soundfonts as each soundfont is loaded with Fluidsynth in order to extract its program information.

The *Apply and Quick Scan* button leaves the soundfonts already in the database intact and only scans and loads new files not yet in the database.



Library
=======

In order to fill the library with instruments (patches, SFZs and sf2 soundfonts), a scan must first be performed from the settings screen.

The library organizes sounds using subdirectories. Thus, for easy navigation it is useful to sort your sounds into subfolders, for example using categories like Piano, Strings, Organs, Pads, etc.

When selecting a soundfont, the list of programs appear below the library tree. By double-clicking on a soundfont program or a SFZ or patch in the tree, the sound is added as a layer to the current patch.

When searching, file names and program names within soundfonts are searched.



Projects
========

A Konfyt project contains the following:

* Patches
* Ports (MIDI and audio input and output ports) with corresponding connections
* Audio input ports and output buses
* List of external applications
* Triggers - actions that are triggered by MIDI events
* List of "Other JACK Connections" - pairs of ports not belonging to Konfyt that will be persistently kept connected

Each project is saved in its own directory. A project directory contains the project file - an XML file with a name ending with ".konfytproject" - and a "patches" folder containing the patches.



Ports and Buses
===============

Konfyt uses ports and buses to receive and send audio and MIDI. A bus is actually just an audio output port. Each port and bus directly relates to a JACK port and can be connected to other JACK ports (i.e. other applications or hardware input/output).

Any port connections specified within Konfyt are persistently maintained, even after other applications restart, hardware is reconnected or when disconnects are attempted from outside Konfyt.

MIDI Input Ports
----------------

A MIDI input port is how Konfyt receives MIDI input from a hardware MIDI controller
(e.g. keyboard) or other applications. The MIDI input is routed to one or more
instrument layers inside patches. MIDI input ports are set up in the *Ports and Buses* screen.

A MIDI input port also has a MIDI filter.

Audio Bus (Output Port)
-----------------------

A bus is an audio output port which relates to 2 JACK audio ports (left and right).
Audio buses output audio to other applications or to the system output. Buses are set up
in the *Ports and Buses* screen. Each instrument layer outputs to a specific bus. Although a new project contains a default *Master Bus*, this is merely a name and there is nothing special about it.

MIDI Output Ports
-----------------

A MIDI output port sends MIDI out from Konfyt to another application or hardware.
To use a MIDI output port, it is added as a layer in a patch. Thus, MIDI will only be sent to the port when a patch is active with that contains a layer corresponding to the port. As a layer, it has its own MIDI filter, output destination port and output MIDI channel specific to that layer (i.e. it can be different for each patch).

Audio Input Ports
-----------------

An audio input port receives audio from other applications or hardware and routes it to a bus.
To use an audio input port, it is added as a layer in a patch. Thus, audio will only be routed from an audio input port when a patch is active that contains a layer corresponding to that port. As a layer, it has its own gain slider and destination bus specific to that layer (i.e. it can be different for each patch).



MIDI Triggers
=============

Konfyt allows MIDI triggers (similar to "MIDI learn" in other applications) to be set up in order to perform an action when the specified MIDI message is received. MIDI triggers are set up in the *Triggers* screen. Received MIDI messages are shown on the right and can be assigned to actions on the left by using the *Assign* button or by selecting the event and double-clicking on the action (or vice versa).

When bank select messages (CC0 and CC32) are directly followed by a program change message, the messages are grouped together as one bank and program message.

MIDI message values are interpreted corresponding to the action it is assigned. For actions such as gain, the absolute MIDI value is used. For other actions such as patch switching or toggling a setting, the action is only triggered if the MIDI message value is larger than zero. This eliminates double triggering when a button or note sends both 127 and zero when pressed.

MIDI events from all MIDI input ports are used for triggers.

Triggers that relate to patch layers will only affect the layers of the currently active patch.

In addition to actions/triggers, the *Triggers* screen contains additional options that are saved in the project:

* *Program Change messages with no bank select switch patches*: When this is enabled, if a program change MIDI
  message is received on its own (without any preceding bank select messages), the patch will be changed based
  on the message program number.
* *Slider MIDI Pickup Range* specifies the range in which sliders will jump to the value of received MIDI messages.
  A maximum range of 127 means that a slider will jump to any received MIDI message value. Lower ranges mean the
  slider will only jump to ("pickup") the value when the difference between the slider value and the received
  MIDI message value is in the range.



Patch/layers View
=================

The main patch/layers view shows the currently active patch. Normally, audio and MIDI will only play from the
currently active (currently visible) patch. Switching to another patch will deactivate the patch and activate
the other patch. When switching away from a patch, audio output ports are faded out so a sudden audio drop isn't
heard. For instrument layers with MIDI input and audio output, their sound will continue to be heard if notes
or a sustain pedal are being held down. When the notes or sustain pedal are lifted, the appropriate messages are
passed to the inactive patch.

A patch can be set as *always active* from the *Patch Menu*. This will keep the patch active even when you switch
to other patches.

Below the layers section is a *Note* section in which you can place text that will be saved with the patch.

MIDI output port layers have a *MIDI Send List*, which is a list of MIDI messages which will be sent out on the
layer whenever the patch is activated. This is useful for switching programs on hardware when activating a patch.



Other JACK Connections
======================

In the *Other Jack Connections* screen, JACK audio and MIDI ports not belonging to Konfyt can be connected
to each other. Just like with Konfyt ports, these connections are persistently maintianed by Konfyt, even
when another app tries to disconnect it or after other apps restart or hardware is reconnected.



External Applications
=====================

The *External Applications* list is a simple list that allows you to store commands in a project for easily running external applications. It can be used as a simple crude way to restore your session of applications every time you open the project.

The string ``$PROJ_DIR$`` will be replaced by the current project directory. This can be used to make a project more self-contained by storing files used by external applications in the Konfyt project directory and using the string in arguments for the commands.

**For instance**, you may use Carla to host plugins:

    For synth plugins, MIDI output port layers send MIDI data from Konfyt to
    Carla and the synth audio is sent back to Konfyt using audio input port
    layers. For effect plugins, a Konfyt bus sends audio to the plugin.

    The external application command ``carla /path/to/my_carla_project.carxp``
    is added to the *External Applications* list in order to quickly launch
    Carla next time with the correct project. However, another option is to
    save the Carla project file in your Konfyt project directory. Then, go to
    the *Filesystem* tab on the left-hand side of the Konfyt window, click on
    the *Project Directory* button, right-click on the Carla project file and
    select *Add Path to External App Box (Relative to Project)*. This adds the
    path of the Carla project file to the *External Applications* text box using
    the string ``$PROJ_DIR$`` to indicate that the file is relative to the
    Konfyt project directory. Just add "carla " in front of the path so that it
    becomes ``carla "$PROJ_DIR$/my_carla_project.carxp"`` and click *Add* to
    add it to the *External Applications* list.



