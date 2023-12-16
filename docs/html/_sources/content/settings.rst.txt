Settings
########

It is a good idea to fill in all the options in the settings screen.


Projects Directory
------------------

This is the default directory for projects. This directory is scanned at startup 
and all the projects are listed in the projects Open menu for easy access. 

When saving a project you can seamlessly save it in this directory by accepting 
the proposed path when asked (or choose No to manually select a different path).


File Manager
------------

The file manager entry is optional and is provided in case your default file 
manager doesn't play along well. You can test it by right-clicking on one of the 
library items and clicking *Open in File Manager*. If you receive an error 
message from your file manager, specify your preferred file manager in settings 
(e.g. either dolphin, nautilus, thunar, pcmanfm, etc.).


Scanning soundfonts, patches and SFZ directories
------------------------------------------------

The soundfonts, patches and samples directories specifiy the directories that
will be scanned to populate the libarary.

The *Apply and Rescan* button clears the library database and scans the specified
directories and subdirectories for SFZs, GIGs, soundfonts (sf2) and patches. 
This may take a while, especially with big soundfonts as each soundfont is 
loaded with Fluidsynth in order to extract its program information.

The *Apply and Quick Scan* button leaves the soundfonts that are already in the 
database intact and only scans and loads new files that are not yet in the database.



