qad-tcp-checker
===============

Quick and dirty http server connection status checker

== Background ==
Nodes in some load balanced web servers were taking turns going down.  They
were taking too long to respond to TCP connections.

I didn't have any graphing or monitoring.  I wrote something quickly to tell
me when a server was taking too long to respond.  Then I could login and
debug.

This program prints a warning when the connection does not complete in 1
second.  I also added a signal handler to dump a summary of the connection
statistics.

== Sample output ==

  $ ./qad-tcp-checker  
  ./qad-tcp-checker is starting as pid 27925.  From another window you may run:
    kill -USR1 27925  
  .................................................................................................................................................Could not create socket to 10.63.243.107 : Connection timed out
  
  -- 8< -- output removed here -- 8< --
  
      10.3.7.62: failures: 103 successes: 1092
     10.3.7.109: failures: 79 successes: 1116
      10.3.7.78: failures: 78 successes: 1117
     10.3.7.105: failures: 29 successes: 1166
     10.3.7.108: failures: 28 successes: 1167
     10.3.7.106: failures: 6 successes: 1189
      10.3.7.79: failures: 3 successes: 1192
      10.3.7.63: failures: 2 successes: 1193
      10.3.7.60: failures: 1 successes: 1194
     10.3.7.107: failures: 1 successes: 1194
      10.3.7.61: failures: 0 successes: 1195

