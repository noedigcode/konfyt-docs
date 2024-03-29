Konfyt Documentation
====================
Digital Keyboard Workstation for Linux
--------------------------------------

This documentation is hosted on GitHub pages from the `docs` folder in this repo:

https://noedigcode.github.io/konfyt-docs/

(Old Sphinx documentation is hosted at https://konfyt.readthedocs.io but since
they changed their build requirements it doesn't build correctly anymore.)

Konfyt source code: https://github.com/noedigcode/konfyt

Konfyt website: http://noedig.co.za/konfyt


Building the documentation
--------------------------

- Ensure Sphinx is installed: `apt install python3-sphinx`

- Install the Sphinx RTD (Read The Docs) theme: `pip install sphinx-rtd-theme`
  
  (A downloaded version is saved in the `_themes` directory for posterity.)

- Build the documentation with `make html`

- Build and copy the documentation to the `docs` dir (for GitHub pages):
  `make github` (includes make html above)

- Ensure the docs dir contains a `.nojekyll` file to prevent GitHub from trying
  to process this.


Conventions and rst cheatsheet
------------------------------

```
Chapter Heading (at top of .rst file)
####################################

Section
=======

Subsection
----------

Strings from the GUI are made *italic* like *Button Text* or *Menu Names*, etc.

Inline code tags are used for ``command`` or ``path`` strings.

**Bold is done like this**

    And indented blocks
    are simply indented
    like so.

* List
* Bullet
* Points

.. Comments are done like so
   and will not appear in the documentation.

| And to force a newline but not a new paragraph (as an empty line would do)
| a line block can be made like this using the pipe characters.


```
