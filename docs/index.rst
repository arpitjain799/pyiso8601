pyiso8601: ISO 8601 Parsing for Python
======================================

Documentation: https://pyiso8601.readthedocs.org/

PyPI: https://pypi.org/project/iso8601/

Source: https://github.com/micktwomey/pyiso8601

This module parses the most common forms of ISO 8601 date strings (e.g. 2007-01-14T20:34:22+00:00) into datetime objects.

>>> import iso8601
>>> iso8601.parse_date("2007-01-25T12:00:00Z")
datetime.datetime(2007, 1, 25, 12, 0, tzinfo=<iso8601.Utc>)
>>>

See the LICENSE file for the license this package is released under.

If you want more full featured parsing look at:

- https://arrow.readthedocs.io - arrow
- https://pendulum.eustace.io - pendulum
- https://labix.org/python-dateutil - python-dateutil
- https://docs.python.org/3/library/datetime.html#datetime.datetime.fromisoformat - Yes, Python 3 has built in parsing too!

Parsed Formats
==============

You can parse full date + times, or just the date. In both cases a datetime instance is returned but with missing times defaulting to 0, and missing days / months defaulting to 1.

Dates
-----

- YYYY-MM-DD
- YYYYMMDD
- YYYY-MM (defaults to 1 for the day)
- YYYY (defaults to 1 for month and day)

Times
-----

- hh:mm:ss.nn
- hhmmss.nn
- hh:mm (defaults to 0 for seconds)
- hhmm (defaults to 0 for seconds)
- hh (defaults to 0 for minutes and seconds)

Time Zones
----------

- Nothing, will use the default timezone given (which in turn defaults to UTC).
- Z (UTC)
- +/-hh:mm
- +/-hhmm
- +/-hh

Where it Differs From ISO 8601
==============================

Known differences from the ISO 8601 spec:

- You can use a " " (space) instead of T for separating date from time.
- Days and months without a leading 0 (2 vs 02) will be parsed.
- If time zone information is omitted the default time zone given is used (which in turn defaults to UTC). Use a default of None to yield naive datetime instances.

References
==========

- https://en.wikipedia.org/wiki/ISO_8601

- https://www.cl.cam.ac.uk/~mgk25/iso-time.html - simple overview

- https://web.archive.org/web/20090309040208/http://hydracen.com/dx/iso8601.htm - more detailed enumeration of valid formats.

Installation
============

To install simply use pip::

    pip install iso8601


API
===

.. autofunction:: iso8601.is_iso8601

.. autofunction:: iso8601.parse_date

.. autoexception:: iso8601.ParseError

