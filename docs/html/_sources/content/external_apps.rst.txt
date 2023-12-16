External Applications
#####################

The *External Applications* list allows you to store 
commands in a project for easily running external applications.
An external application can be run on demand at any time, or can be set to
start automatically when you open the project.
You can also set to automatically relaunch an application when it stops (or
crashes).

In the external app editor, the *Name* text box specifies a friendly name that
will be dispayed in the list, but has nothing to do with the app.

The *Command* text box contains the command and arguments that will be run when
the app is launched. You can edit this text manually. Its drop down menu contains
useful preset applications and other options.

In the external app command, the string ``$PROJ_DIR$`` will be replaced by the 
current project directory.
This can be used to make a project more self-contained (and insensitive to being
moved around) by storing files used by external applications in the Konfyt 
project directory and using the above string in arguments for the commands.

In the *Filesystem* tab on the left-hand side of the Konfyt window, you can
right-click on any file or directory and use one of the
*Add Path to External App Command* entries to easily add paths to the external
app command.

