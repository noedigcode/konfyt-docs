MIDI Filters
############

A MIDI filter filters and/or modifies MIDI messages. MIDI filters are available
for MIDI input ports (on the *Ports and Buses* screen), patches (from the
*Patch Menu*) and individual patch layers that have MIDI input.

Velocity Map
------------

The *Velocity Map* modifies incoming note velocities according to a mapping.
The mapping is defined by a series of input velocities and a series of output
velocities, separated with a semicolon:

``in1 in2 in3 ... inx; out1 out2 out3 ... outx``

where input values are mapped to the output values. Values in-between are linearly
interpolated.

Presets are provided for common velocity curves.

With appropriate values, the map can also be set up to block notes with certain
velocities, limit the minimum or maximum velocity or compress the velocity
range.

For instance, the following mapping limits the minimum velocity to 30, so notes
softer than 30 will be raised to 30 while the rest are left unchanged:

``0 30 127; 30 30 127``

The following mapping limits the maximum velocity to 100. All louder notes will
be changed to 100.

``0 100 127; 0 100 100``

This mapping will block all notes with a velocity lower than 50:

``0 50 50 127; 0 0 50 127``

