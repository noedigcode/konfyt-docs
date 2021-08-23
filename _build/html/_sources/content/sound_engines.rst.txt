Sound Engines
#############

Konfyt fundamentally uses JACK (the JACK Audio Connection Kit) for MIDI and audio.

Fluidsynth is used to load, inspect and play sf2 soundfont files.

Konfyt initially used only Carla for handling SFZ instruments. At the time, Carla
still used Linuxsampler as a backend for playing SFZs. However, the Linuxsampler
support became troublesome and (among other reasons) Carla moved to SFZero for
handling SFZ. Finding the SFZ support of SFZero lacking, I implemented Linuxsampler
support using the LSCP (Linuxsampler Control Protocol) library.

Currently Konfyt supports both Carla and Linuxsampler backends for SFZ.
Linuxsampler is used by default if no command-line arguments are specified.

Linuxsampler
------------

LSCP is used to communicate with Linuxsampler. At startup, if LSCP fails to
initialise, it is assumed that Linuxsampler is not running and a Linuxsampler
process is started. Then LSCP initialisation is retried.

Linuxsampler audio and MIDI JACK engines are created. The JACK client name is
derived from Konfyt's JACK client name. If Linuxsampler engines with the same
name already exists, it is assumed to be from a previous Konfyt instance that
is no longer running and the engines and related SFZ instruments are removed
before new ones are created for the current session.

Multiple instances of Konfyt can coexist since JACK requires that each client
have a unique name.

When a SFZ layer is added in Konfyt, the instrument is loaded in Linuxsampler
via LSCP. A MIDI port and two audio ports are created for the instrument in Linuxsampler.
Konfyt also creates MIDI and audio ports specifically for the SFZ layer and
automatically connects these to the Linuxsampler ports in order to transfer MIDI and audio
between Konfyt and Linuxsampler.

Carla
-----

If the user wants to use Carla for SFZ support, the appropriate command-line
argument must be passed to Konfyt at startup. Use ``--help`` for more details.

The Carla backend runs inside Konfyt but MIDI and audio are exchanged similar to
with Linuxsampler, using JACK ports.

