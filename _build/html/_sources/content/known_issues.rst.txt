Known Issues
############

MIDI Triggers not working when screen locked
--------------------------------------------

2021-08-23, Linux Mint 20.2, Xfce, Light Locker, Qt 5.12.8

When the screen is locked, MIDI triggers do not work and the actions are only
performed once the screen is unlocked.

This is due to a Qt bug causing the GUI and timers to stop while the screen is
locked.

A workaround is to set the following environment variable before running Konfyt:
``export QT_XCB_GL_INTEGRATION=none``

Discussions on this Qt bug can be found here:

- https://bugreports.qt.io/browse/QTBUG-47179?attachmentViewMode=list
- https://bugs.freedesktop.org/show_bug.cgi?id=91448
- https://gitlab.freedesktop.org/xorg/xserver/-/issues/206
- https://gitlab.freedesktop.org/xorg/xserver/-/issues/497


No sound, JACK complains that it can't allocate memory, crash (pre v1.2.2)
--------------------------------------------------------------------------

If the following is printed when running Konfyt from a console:
``
Cannot lock down 82280346 byte memory area (Cannot allocate memory)
``
along with potentially other memory or realtime related messages, your system
may not be configured correctly for realtime audio work.

Two probable culprits are that your user may not be in the ``audio`` group, and
that your ``ulimits`` file may not be set up correctly.

The rtcqs script from https://codeberg.org/rtcqs/rtcqs can be used to check
whether your system is set up properly. Follow the guidelines in the script
(especially related to the above mentioned) to make the required changes.


