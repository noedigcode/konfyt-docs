Scripting
#########

JavaScript scripting for patch layers was added as an experiment in Konfyt version 1.5.0.

Scripting for MIDI input ports was added in version 1.6.0.

Patch layers with MIDI input and MIDI input ports have optional scripts that can
process incoming MIDI events. Script processing happens after MIDI filters. For
ports, script processing also happens before MIDI is sent to triggers and patches.

Scripts are evaluated in a separate thread from the GUI and JACK processing threads.
This means that scripts will not affect normal non-script MIDI and audio processing
or freeze the GUI.

This does mean, however, that script processing is not strictly real-time.
However, initial testing hasn't found any noticeable delay or other issues.

For patch layers, scripts are accessible by selecting "Edit Script" from the
layer's menu (left-hand side button). For MIDI input ports, when the port is
selected on the *Ports and Buses* screen, a button to access
the script editor for the port appears below the connections list.

By default, scripts are disabled, meaning no processing is happening
with regards to that script.

Each script has a "Pass Original MIDI Through" option which sets whether all
incoming MIDI is sent to the output in in parallel with the script, or whether
incoming MIDI is blocked and only passed to the script.

The scripting API documentation is given in Konfyt next to the script editor.

Each enabled script will receive MIDI events after they have passed through
the layer's or port's MIDI filter. MIDI events sent from the script with
``Midi.send()`` are sent down the chain. For layers, events are sent to the
layer's assigned output port. For ports, events are sent to triggers and patches.

Currently it is not possible to
handle notes, sustain and pitchbend in the same way as normal non-script MIDI
events when changing patches. Thus, when a script outputs a note-on, sustain
or pitchbend message, and another patch is activated, no corresponding note-off,
sustain zero or pitchbend zero messages will be sent.

A script must define two functions that are called by Konfyt: ``init()`` and ``midiEvent(ev)``.
When a script is enabled or updated, the ``init`` function is called once.
For each incoming MIDI message, the ``midiEvent`` function is called where the
``ev`` argument is the incoming MIDI message.

When execution of a script takes too long, a script is stopped and not executed
for further incoming MIDI events, until it is updated or enabled again.
The same is done when an error occurs during evaluation.
When this happens, information is output in the console and a warning is displayed
in the *Warnings* list in the right-hand side of the Konfyt window. Double-clicking
on the warning will open the corresponding script editor.

Patch layer scripts are referred to with a short ID (or URI) in the format ``PxLy``,
where ``x`` refers to the patch number starting at 1, and ``y`` refers to the
layer number starting at 1. "P3L5" refers to the script of layer 5 in patch 3.

