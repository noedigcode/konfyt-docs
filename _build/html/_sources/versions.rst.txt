What's New
===============

v1.1.2
------

14 October 2020

* Per-layer MIDI indicators (activity, sustain and pitchbend non-zero).

* Global sustain and pitchbend non-zero indicators.

* Fairly big code refactor under the hood, should not be noticeable to users.

* Fix bug of empty MIDI input ports added after removal of non-last port while
  console MIDI output is enabled.

* Small GUI tweaks.



v1.1.1
------

10 October 2020

* Preview mode options: MIDI input port and channel, output bus.

* MIDI input port and bus menus now have a link to the connections page.

* Save-as finally implemented.

* Compatible with Carla 2.2.0 (API change).

* Default global and layer gain (volume) is now 1.0.

* SF3 soundfonts are now detected and loaded.

* Current setting is marked in MIDI channel/port/bus menus.

* Small GUI tweaks.



v1.1.0
------

27 December 2019

* MIDI send events: each MIDI output layer can have MIDI send events associated
  with it which are sent when the patch is activated. MIDI send events can also
  be saved for future use in other projects.

* MIDI note names octave numbers changed to the IPN standard to match most other
  software numbering.

* Always-active option for patches: a patch can be set to always be active, even
  if it is not the current patch.

* GUI uses system specified font size and resizes properly based on font size.

* Fluidsynth 2 support.

* Config files saved to standard XDG directories.

* Carla support optional.

