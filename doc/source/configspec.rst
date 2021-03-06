
The [calendars] section
~~~~~~~~~~~~~~~~~~~~~~~

The *[calendars]* is mandatory and must contain at least one subsection.
Every subsection must have a unique name (enclosed by two square brackets).
Each subection needs exactly one *path* setting, everything else is optional.
Here is a small example:

.. literalinclude:: ../../tests/configs/small.conf
 :language: ini

.. _calendars-color:

.. object:: color

    
    khal will use this color for coloring this calendar's event. Depending on
    your terminal emulator's settings, they might look different than what their
    name implies.

      :type: option, allowed values are *black*, *white*, *brown*, *yellow*, *dark grey*, *dark green*, *dark blue*, *light grey*, *light green*, *light blue*, *dark magenta*, *dark cyan*, *dark red*, *light magenta*, *light cyan*, *light red* and **
      :default: 

.. _calendars-path:

.. object:: path

    the path to a *vdir* where this calendar is saved

      :type: string
      :default: None

.. _calendars-readonly:

.. object:: readonly

    
    setting this to *True*, will keep khal from making any changes to this
    calendar

      :type: boolean
      :default: False

.. _calendars-type:

.. object:: type

    
    Set the type of this collection, the default is ``calendar``.
    If set to ``birthdays`` khal will expect a VCARD collection and extract
    birthdays from those VCARDS. ``birthdays`` also implies ``readonly=True``.

      :type: option, allowed values are *calendar* and *birthdays*
      :default: calendar

The [sqlite] section
~~~~~~~~~~~~~~~~~~~~


.. _sqlite-path:

.. object:: path

    khal stores its internal caching database here, by default this will be in the *$XDG_DATA_HOME/khal/khal.db* (this will most likely be *~/.local/share/khal/khal.db*).

      :type: string
      :default: None

The [locale] section
~~~~~~~~~~~~~~~~~~~~

The most important options in the the **[locale]** section are probably (long-)time and dateformat.

.. _locale-encoding:

.. object:: encoding

    
    set this to the encoding of your terminal emulator

      :type: string
      :default: utf-8

.. _locale-local_timezone:

.. object:: local_timezone

    
    khal will show all times in this timezone
    If no timezone is set, the timezone your computer is set to will be used.

      :type: timezone
      :default: None

.. _locale-unicode_symbols:

.. object:: unicode_symbols

    
    by default khal uses some unicode symbols (as in 'non-ascii') as indicators for things like repeating events,
    if your font, encoding etc. does not support those symbols, set this to *False* (this will enable ascii based replacements).

      :type: boolean
      :default: True

.. _locale-longdateformat:

.. object:: longdateformat

    
    khal will display and understand all dates in this format, it should
    contain a year (e.g. *%Y*) see :ref:`timeformat <locale-timeformat>` for the format.

      :type: string
      :default: %d.%m.%Y

.. _locale-longdatetimeformat:

.. object:: longdatetimeformat

    
    khal will display and understand all datetimes in this format, it should
    contain a year (e.g. *%Y*) see :ref:`timeformat <locale-timeformat>` for the format.

      :type: string
      :default: %d.%m.%Y %H:%M

.. _locale-default_timezone:

.. object:: default_timezone

    
    this timezone will be used for new events (when no timezone is specified) and
    when khal does not understand the timezone specified in the icalendar file.
    If no timezone is set, the timezone your computer is set to will be used.

      :type: timezone
      :default: None

.. _locale-datetimeformat:

.. object:: datetimeformat

    
    khal will display and understand all datetimes in this format, see
    :ref:`timeformat <locale-timeformat>` for the format.

      :type: string
      :default: %d.%m. %H:%M

.. _locale-weeknumbers:

.. object:: weeknumbers

    
    
    Enable weeknumbers in `calendar` and `interactive` (ikhal) mode. As those are
    iso weeknumbers, they only work properly if `firstweekday` is set to 0

      :type: weeknumbers
      :default: off

.. _locale-timeformat:

.. object:: timeformat

    
    khal will display and understand all times in this format.
    
    The formatting string is interpreted as defined by Python's `strftime
    <https://docs.python.org/2/library/time.html#time.strftime>`_, which is
    similar to the format specified in ``man strftime``.

      :type: string
      :default: %H:%M

.. _locale-dateformat:

.. object:: dateformat

    
    khal will display and understand all dates in this format, see :ref:`timeformat <locale-timeformat>` for the format

      :type: string
      :default: %d.%m.

.. _locale-firstweekday:

.. object:: firstweekday

    
    the day first day of the week, were Monday is 0 and Sunday is 6

      :type: integer, allowed values are between 0 and 6
      :default: 0

The [keybindings] section
~~~~~~~~~~~~~~~~~~~~~~~~~

keybindings for :command:`ikhal` are set here. You can bind more than one key
(combination) to a command by supplying a comma-seperated list of keys.
For binding key combinations just add concatenate them (with a space in
between), e.g. **ctrl n**.

.. _keybindings-save:

.. object:: save

    
    save the currently edited event and leave the event editor

      :type: list
      :default: meta enter

.. _keybindings-right:

.. object:: right

    
    move the cursor right (in the calendar browser)

      :type: list
      :default: right, l, space

.. _keybindings-view:

.. object:: view

    
    show details or edit (if details are already shown) the currently selected event

      :type: list
      :default: enter, tab

.. _keybindings-up:

.. object:: up

    
    move the cursor up (in the calendar browser)

      :type: list
      :default: up, k

.. _keybindings-down:

.. object:: down

    
    move the cursor down (in the calendar browser)

      :type: list
      :default: down, j

.. _keybindings-duplicate:

.. object:: duplicate

    
    duplicate the currently selected event

      :type: list
      :default: p

.. _keybindings-new:

.. object:: new

    
    create a new event on the selected date

      :type: list
      :default: n

.. _keybindings-left:

.. object:: left

    
    move the cursor left (in the calendar browser)

      :type: list
      :default: left, h, backspace

.. _keybindings-today:

.. object:: today

    
    focus the calendar browser on today

      :type: list
      :default: t

.. _keybindings-delete:

.. object:: delete

    
    delete the currently selected event

      :type: list
      :default: d

The [default] section
~~~~~~~~~~~~~~~~~~~~~

The default section begins with a **[default]** tag. Some default values and
behaviours are set here.

.. _default-default_command:

.. object:: default_command

    
    command to be executed if no command is given when executing khal

      :type: option, allowed values are *calendar*, *agenda*, *interactive*, *printformats*, *printcalendars* and **
      :default: calendar

.. _default-print_new:

.. object:: print_new

    
    After adding a new event, what should be printed to standard out? The whole
    event in text form, the path to where the event is now saved or nothing?

      :type: option, allowed values are *event*, *path* and *False*
      :default: False

.. _default-days:

.. object:: days

    
    By default, khal show events for today and tomorrow.
    Setting this to a different value will show events of that amount of days by
    defaut.

      :type: integer
      :default: 2

.. _default-highlight_event_days:

.. object:: highlight_event_days

    
    If true, khal will highlight days with events. Options for
    highlighting are in [highlight_days] section.

      :type: boolean
      :default: False

.. _default-default_calendar:

.. object:: default_calendar

    
    The calendar to use if none is specified for some operation (e.g. if adding a
    new event). If this is not set, such operations requre an explicit value.

      :type: string
      :default: None

.. _default-show_all_days:

.. object:: show_all_days

    
    By default, khal displays only dates with event in "agenda" view.
    Setting this to *True* will show all days in "agenda", even
    when there is no event

      :type: boolean
      :default: False

The [view] section
~~~~~~~~~~~~~~~~~~

The view section contains config options that effect the visual appearance
when using ikhal

.. _view-event_view_weighting:

.. object:: event_view_weighting

    
    This is the weighting that is applied to the event view window

      :type: integer
      :default: 1

.. _view-theme:

.. object:: theme

    
    Choose a color theme for khal.
    
    This is very much work in progress. Help is really welcome! The two currently
    available color schemes (*dark* and *light*) are defined in
    *khal/ui/themes.py*, you can either help improve those or create a new one
    (see below). As ikhal uses urwid, have a look at `urwid's documentation`__
    for how to set colors and/or at the existing schemes. If you cannot change
    the color of an element (or have any other problems) please open an issue on
    github_.
    
    If you want to create your own color scheme, just copy the structure of the
    existing ones, give it a new and unique name and also add it as an option in
    `khal/settings/khal.spec` in the section `[default]` of the property `theme`.
    
    __ http://urwid.org/manual/displayattributes.html
    .. _github: # https://github.com/geier/khal/issues

      :type: option, allowed values are *dark* and *light*
      :default: dark

.. _view-frame:

.. object:: frame

    
    Whether to show a visible frame (with *box drawing* characters) around some
    (groups of) elements.

      :type: boolean
      :default: False

.. _view-event_view_always_visible:

.. object:: event_view_always_visible

    
    Set to true to always show the event view window when looking at the event list

      :type: boolean
      :default: False

The [highlight_days] section
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When highlight_event_days is enabled, this section specifies how is
the highlighting rendered.

.. _highlight_days-color:

.. object:: color

    
    What color to use when highlighting - explicit color or use calendar
    color when set to ''

      :type: option, allowed values are *black*, *white*, *brown*, *yellow*, *dark grey*, *dark green*, *dark blue*, *light grey*, *light green*, *light blue*, *dark magenta*, *dark cyan*, *dark red*, *light magenta*, *light cyan*, *light red* and **
      :default: 

.. _highlight_days-multiple:

.. object:: multiple

    
    How to color days with events from multiple calendars - either
    explicit color or use calendars' colors when set to ''

      :type: option, allowed values are *black*, *white*, *brown*, *yellow*, *dark grey*, *dark green*, *dark blue*, *light grey*, *light green*, *light blue*, *dark magenta*, *dark cyan*, *dark red*, *light magenta*, *light cyan*, *light red* and **
      :default: 

.. _highlight_days-method:

.. object:: method

    
    Highlighting method to use - foreground or background

      :type: option, allowed values are *foreground*, *fg*, *background* and *bg*
      :default: fg

.. _highlight_days-default_color:

.. object:: default_color

    
    Default color for calendars without color - when se to '' it
    actually disables highlighting for events that should use the
    default color.

      :type: option, allowed values are *black*, *white*, *brown*, *yellow*, *dark grey*, *dark green*, *dark blue*, *light grey*, *light green*, *light blue*, *dark magenta*, *dark cyan*, *dark red*, *light magenta*, *light cyan*, *light red* and **
      :default: 
