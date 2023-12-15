Projects
########

A Konfyt project contains the following:

* Patches (containing layers)
* Ports (MIDI and audio input and output ports) with corresponding connections
* List of external applications
* Triggers - actions that are triggered by MIDI events
* List of "Other JACK Connections"


Each project is saved in its own directory. A project directory contains the 
project file (an XML file with a name ending with ".konfytproject") and a 
"patches" folder containing the patches.


Backups
-------

Since Konfyt 1.5.0, when saving a project, a backup of the project is made
before saving (presave) and after saving (postsave). Backups are placed in a
"backup" subfolder in the project directory.

Backups allow recovery of data when you accidentally made changes to the project
or when when a project has been modified by other versions of Konfyt, causing
some data to be lost.

Konfyt versions are backwards compatible with project files of previous versions.
However, when previous versions of Konfyt open a project file created with a
later version, it will ignore any data that isn't supported in that version and,
when saving, that data will be discarded.

By creating presave and postsave backups, this can hopefully be guarded against.
When Konfyt (since version 1.5.0) opens a project of a later version and saves
it, the presave backup will contain all the data of the later version that will
be discarded by the save.

When a previous version of Konfyt (that doesn't yet do backups) opens
a version 1.5.0+ project and saves it, no backup will be created, but the
last saved version 1.5.0+ project will still be available as a postsave backup
(that was created the last time the project was saved by a 1.5.0+ version of
Konfyt).


