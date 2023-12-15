Patches
#######

The main patch/layers view shows a list of patches and the currently active patch. 

Normally, audio and MIDI will only play from the currently active (currently 
visible) patch. Switching to another patch will deactivate the patch and activate
the other patch. When switching away from a patch, audio output ports are faded 
out so a sudden audio drop isn't heard. 
For instrument layers with MIDI input and audio output, their sound will continue
to be heard if notes or a sustain pedal are being held down. When the notes or 
sustain pedal are lifted, the appropriate messages are passed to the inactive patch.

A patch can be set as *always active* from the *Patch Menu*. This will keep the 
patch active even when you switch to other patches.

Below the layers section is a *Note* section in which you can place text that 
will be saved with the patch.

A patch has a MIDI filter (accessible from the *Patch Menu*) which filters the
MIDI patch-wide before reaching any of the layers.

Layers
------

A patch consists of one or more layers. The following types of layers are
possible:

- Instrument layers: SFZ or soundfont
- MIDI output port: routes MIDI from a MIDI input port to a MIDI output port.
  The layer is fixed to a MIDI output port. The MIDI input port can be selected.
- Audio input port layer: routes audio from an audio input port to an audio
  output bus. The layer is fixed to an audio input port. The output bus can be
  selected.

Layers with MIDI input each have a MIDI filter and a script.

MIDI output port layers have a *MIDI Send List*, which is a list of MIDI messages 
that will be sent out on the layer whenever the patch is activated. 
This is useful for switching programs or settings on external synths when 
activating a patch.


