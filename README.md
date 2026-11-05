# spectroscopy-star-finder

A star finder that locates visible stars by spectral class.

This file is written in Python.

Visible Stars by Spectral Class  (GUI)
======================================

Enter a location, a date and time, a number N, and tick the spectral classes you want (O B A F G K M).
The program lists N stars of each chosen class that are above the horizon and bright enough to see at
that place and time (brightest first by default), shows them in a table and on an all-sky chart, and
can save the list as a CSV file.

- Requirements:   pip install numpy astropy matplotlib
- Recommended:    pip install geopy timezonefinder
                (geopy turns a place name into coordinates, timezonefinder finds the time zone; without
                 them type "latitude, longitude" and a UTC offset instead)

- Star data:      the HYG database (Hipparcos / Yale Bright Star / Gliese catalogues combined, with proper
                names and spectral types). It is downloaded once (about 34 MB) and a small cached copy is
                kept in  ~/.cache/visible_stars/ . If the download is blocked, fetch hygdata_v41.csv in a
                browser and choose it with the "Catalogue file…" button.

- Run:            python visible-stars-by-class.py

Notes on "visible":
  * a star counts as visible when it is at least "Minimum altitude" degrees above the horizon and brighter
    than the limiting magnitude (6.0 is a dark rural sky). When the Sun is up or the sky is in twilight the
    limit is made shallower (rough estimates; tick "Ignore daylight / twilight" to switch this off).
  * the Moon, clouds, light pollution and terrain are not considered.
  * positions use J2000 catalogue coordinates (proper motion is ignored: well under an arc-minute for
    nearly all naked-eye stars).
"""
