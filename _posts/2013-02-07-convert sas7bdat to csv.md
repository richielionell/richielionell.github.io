---
layout: post
title: Convert sas7bdat to CSV
---

Had to convert a 450mb odd sas7bdat file to csv the other day and came across two methods that worked without a hitch.

Method 1:

1. Download the [SAS System Viewer](http://support.sas.com/demosdownloads/sysdep_t1.jsp?packageID=000176) (free)
2. Under File > Open, select the sas7dbat file. 
3. Once the file loads, select File > Save as file .. 'save as csv'

Method 2:

1. Install the trial version of [DsShell](http://www.oview.co.uk/dsshell/)
2. Right click the sas7bdat file and select 'convert dataset to csv'

You could also try  the command-line option [dsread](http://www.oview.co.uk/dsread/).

I'm not sure of size limitations in these tools at the moment, just happy to get the quick and dirty work done.
