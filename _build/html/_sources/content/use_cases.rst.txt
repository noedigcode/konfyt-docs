Use Cases
#########

The first steps
===============

Perform these steps to set up Konfyt and get going:

#. Specify paths in Settings and let your instrument directories be scanned to
   fill the library.

#. In the *Ports and Busses* screen, assign a client to the MIDI input port.
   Access to ALSA hardware can be gained by using the command
   ``a2jmidid -e -u``
   It is also useful to add this command to the *External Applications* list so 
   it can easily be run next time.

#. Test MIDI input by watching the MIDI receive indicator at the top right or by
   selecting *Show MIDI Messages* at the console and watching the console.

#. In the *Ports and Busses* screen, connect the audio bus(es) to system output
   or JACK clients.

#. Add a SFZ or soundfont layer to the patch and test your audio.

#. Remember to enter a project name and save often!



Example with ZynAddSubFX and Ardour
===================================

Konfyt doesn't attempt to do everything itself but works in harmony with other
JACK aware applications. This example shows how Konfyt can be used in combination
with a stand-alone synth application and a plugin host.

#. Create a new Konfyt project, connect the MIDI input port, verify that you 
   receive MIDI and save the project.

   Take note of the project path. If you forgot, you can quickly find it by 
   clicking the *Project Directory* button in the *Filesystem* tab on the
   left-hand side of the Konfyt window.

#. Launch ZynAddSubFX and select or create a desired preset.

#. Save your ZynAddSubFX session (File->Save All Parameters...) to your Konfyt
   project directory as "zyn_lead.xmz" for example.

#. In Konfyt, navigate to the saved file in the *Filesystem* tab, right-click on
   it and select *Add Path To External App Box (Relative to Project)*.
   
   The *External Applications* text box should now contain something like
   "$PROJ_DIR$/zyn_lead.xmz".

#. Add "zynaddsubfx -l " to the beginning of the text. The -l argument tells Zyn
   you want to load the file.

#. Now, in the event that you might use another instance of ZynAddSubFX,
   you want the JACK port names of this instance to be uniquely identifiable and
   remain the same across sessions. To ensure this, add " -N zyn_lead" at the
   end of the command. This makes ZynAddSubFX append the "zyn_lead" string to
   its port names.

   The command should now look like this:
   ``zynaddsubfx -l "$PROJ_DIR$/zyn_lead.xmz" -N zyn_lead``

#. Click *Add* to add it to the list.

#. Close ZynAddSubFX. Then double-click on the newly added entry in the
   *External Applications* list to test it. ZynAddSubFX should start up with the
   appropriate settings loaded from the file.

#. In the *Ports and Busses* screen, add a new MIDI output port, name it
   "zyn lead send" and connect it to the ZynAddSubFX midi_input port.

#. Add an audio input port, name it "zyn lead return" and connect it to the
   ZynAddSubFX out_1 and out_2 ports.

#. Create a new patch and add the newly created MIDI output port and audio input
   port as layers. When you play notes, MIDI is now sent to Zyn and the audio is
   returned to Konfyt. The audio is routed to the output bus specified in the
   audio input port layer.

#. Now, we might want to apply some effects like reverb and EQ to the Zyn audio.
   Open a plugin host, for example Ardour. Create a new project, saving it to
   the Konfyt project directory and adding it as an external application command
   like before. (Note that the -l and -N arguments that were used above are
   specific to Zyn and not applicable to Ardour.)

#. In Ardour, create an audio bus and add reverb and/or other effects plugins to it.

#. In Konfyt, in the *Ports and Busses* screen, add a bus, naming it "Ardour Effects"
   for example and selecting the Ardour audio bus/track as its clients to connect to.

#. In the patch, on the audio input port layer, click the *Bus* button on the
   right hand side and select the newly created bus. Now, the audio from Zyn will
   be routed to Ardour for some cool effects.

Remember to save your Konfyt project regularly.

When done, close Konfyt, Ardour and Zyn, re-open Konfyt, launch Ardour and Zyn
from the *External Applications* list and test that everything still works.
If everything was set up correctly, the JACK port connections should automatically
be connected and everything should work as before.



More ideas
==========

Some applications that might augment your workflow with Konfyt are:

* Carla, Ardour and other plugin hosts.

* mididings, QMidiRoute for more advanced MIDI filtering and routing.

* a2jmidid with the ``-e`` argument to get access to ALSA hardware and software MIDI
  ports and the ``-u`` argument to remove ALSA port numbers from port names.


