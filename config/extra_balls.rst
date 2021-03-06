extra_balls:
============

*Config file section*

.. include:: _machine_config_no.rst
.. include:: _mode_config_yes.rst

.. overview

The ``extra_balls:`` section of your config is where you configure
which events trigger and reset extra ball awards.

Note that this extra ball abstract device is fairly basic right now.
For example, there's no good way to tie this into extra ball "lit"
shots or anything at the moment.

Here's an example:

::

   extra_balls:
       my_mode_eb:
           award_events: alien_smashed
           reset_events: wizard_done

In the above example, the extra ball called ``my_mode_eb`` will be
given to the player when the event ``alien_smashed`` is posted. After that,
future ``alien_smashed`` events will not lead to additional extra balls. (The
``my_mode_eb`` extra ball is "used up", in a sense. However, if the
event ``wizard_done`` is posted, then that would reset this extra ball
and it could be awarded again. (This is very rare, since you don't
want a good player getting the same extra ball over and over.)

This is all tracked per-player in a player variable dictionary called "extra_balls_awarded"

Required settings
-----------------

The following sections are required in the ``extra_balls:`` section of your config:

<name>:
~~~~~~~

Each subsection of ``extra_balls:`` is a name entry for a particular
extra ball award.


Optional settings
-----------------

The following sections are optional in the ``extra_balls:`` section of your config. (If you don't include them, the default will be used).

award_events:
~~~~~~~~~~~~~
List of one or more events (with optional delay timings), in the
:doc:`device control events </config/instructions/device_control_events>` format.
Default: ``None``

Event(s) that will award this extra ball to the current player.

debug:
~~~~~~
Single value, type: ``boolean`` (Yes/No or True/False). Default: ``False``

See the :doc:`documentation on the debug setting </config/instructions/debug>`
for details.

label:
~~~~~~
Single value, type: ``string``. Default: ``%``

A descriptive name for this device which will show up in the service menu
and reports.

reset_events:
~~~~~~~~~~~~~
List of one or more events (with optional delay timings), in the
:doc:`device control events </config/instructions/device_control_events>` format.
Default: ``None``

Event(s) that reset this extra ball, meaning it can be awarded to a player again even
if it has previously been awarded.

tags:
~~~~~
List of one (or more) values, each is a type: ``string``. Default: ``None``


Special / reserved tags for extra balls: *None*

See the :doc:`documentation on tags </config/instructions/tags>` for details.



