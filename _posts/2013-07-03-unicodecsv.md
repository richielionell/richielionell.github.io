---
layout: post
title: unicodecsv
---

If you've worked with python's CSV library you may have come across this error while writing data to csv files;

    UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 23: ordinal not in range(128)

Came across **[unicodecsv](https://pypi.python.org/pypi/unicodecsv/0.9.4)** which helps you overcome the `'UnicodeEncodeError'`. 
Moreover **unicodecsv** has the same syntax as that of csv.writer and csv.reader.
Works fine for now!
