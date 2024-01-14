Ports and Buses
###############

Konfyt uses ports and buses to receive and send audio and MIDI.
A bus is actually just an audio output port. 
Each port and bus directly relates to a JACK port and can be connected to JACK
ports of other applications or hardware.

Any port connections that are specified within Konfyt in the *Ports and Buses*
screen are persistently maintained, even after other applications restart, 
hardware is reconnected or when disconnects are attempted from outside Konfyt.

All ports and buses are set up in the *Ports and Buses* screen. They can then
be assigned to patch layers as input/output in the patch/layer view, by using
the menu buttons in each layer.


MIDI Input Ports
----------------

A MIDI input port is how Konfyt receives MIDI input from a hardware MIDI controller
(e.g. keyboard) or other applications.

A MIDI input port also has its own MIDI filter, which filters all MIDI before it
reaches any patches/layers. When a MIDI input port is selected on the *Ports and Buses*
screen, a button appears below the connections list to access the MIDI filter settings.

Scripting was introduced for MIDI input ports in Konfyt version 1.6.0. This allows
MIDI messages to be processed in a script after the MIDI filter, before it is sent
to triggers and patches. When a MIDI input port is selected on the *Ports and Buses*
screen, a button appears below the connections list to edit the script.

MIDI input is first routed through the port's MIDI filter, then to active patches
through their MIDI filters, and finally to all layers which have been set to use
the port as input.


Audio Bus (Output Port)
-----------------------

A bus is an audio output port which relates to 2 JACK audio ports (left and right).
Audio buses output audio to other applications or to the system output.
Each patch layer with audio output (instrument layers and audio layers) outputs
to a specific bus.

Although a new project contains a default *Master Bus*, this is merely a name and
there is nothing special about it.

An audio bus can be set to ignore (bypass) the global output volume. When an audio bus
is selected on the *Ports and Buses* screen, a checkbox appears below the connections list
to enable this. This is ideal for when you want to send some audio to another application
for applying effects, and loop it back into Konfyt (return) for further routing.
By enabling this option on the "send" bus, the audio level isn't reduced by
Konfyt's Global Volume, preventing it from being reduced multiple times (each time
the signal leaves Konfyt).


MIDI Output Ports
-----------------

A MIDI output port sends MIDI out from Konfyt to another application or hardware.
To use a MIDI output port, it is added as a layer in a patch.
Thus, MIDI will only be sent to the port when a patch is active that contains a 
layer corresponding to the port.


Audio Input Ports
-----------------

An audio input port receives audio from other applications or hardware.
To use an audio input port, it is added as a layer in a patch. 
Thus, audio will only be routed from an audio input port when a patch is active 
that contains a layer corresponding to that port. 
As a layer, it has its own gain slider and destination bus specific to that layer.


