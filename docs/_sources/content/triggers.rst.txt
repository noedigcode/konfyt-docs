MIDI Triggers
#############

Konfyt allows MIDI triggers (similar to "MIDI learn" in other applications) to 
be set up in order to perform an action when the specified MIDI message is received. 
MIDI triggers are set up in the *Triggers* screen. Incoming MIDI messages are 
shown on the right and can be assigned to actions on the left by using the 
*Assign* button or by selecting the event and double-clicking on the action
(or vice versa).

Currently, triggers don't take the source port into account, meaning MIDI messages
matching the trigger from any port will trigger the associated action.

When bank select messages (CC0 and CC32) are directly followed by a program 
change message, the messages are grouped together as one bank and program message.

MIDI message values are interpreted corresponding to the action it is assigned. 
For actions such as gain, the absolute MIDI value is used. Pitchbend values are
mapped to between 0 and 127. For other actions such as patch switching or toggling 
a setting, the action is only triggered if the MIDI message value is larger than 
zero. This eliminates double triggering when a button or note sends both 127 and
zero when pressed.

Triggers that relate to patch layers will only affect the layers of the currently active patch.

In addition to actions/triggers, the *Triggers* screen contains additional options that are saved in the project:

* *Program Change messages with no bank select switch patches*: When this is enabled, if a program change MIDI
  message is received on its own (without any preceding bank select messages), the patch will be changed based
  on the message program number.
* *Slider MIDI Pickup Range* specifies the range in which sliders will jump to the value of received MIDI messages.
  A maximum range of 127 means that a slider will jump to any received MIDI message value. Lower ranges mean the
  slider will only jump to ("pickup") the value when the difference between the slider value and the received
  MIDI message value is in the range.


