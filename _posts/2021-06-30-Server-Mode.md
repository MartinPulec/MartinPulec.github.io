---
layout: post
title: Server Mode
---
[![server](/img/technology-1587673_640.jpg)](https://pixabay.com/)
UltraGrid has a new NAT traversal option utilizing
[UDP hole punching](https://en.wikipedia.org/wiki/UDP_hole_punching).
In this scenario, one side doesn't have public IP or is protected by firewall
while the second, acting as server, does.

As described in [this wiki page](https://github.com/CESNET/UltraGrid/wiki/NAT-traversal#server-mode)
a sender can act as a server meaning that it awaits for incoming connection
from a client. It is not necessary for the server to be a sender but if it was
a receiver only, the scenario would be trivial (no options are needed to send to
a receiver with public IP).

In this mode, UltraGrid can be combined sender/receiver as usual. However, separate
processes are not recommended in the server mode. If still needed, use different ports
(`-P` option) for individual stream directions.

As with normal UltraGrid, this mode is peer-to-peer only, more clients is not possible
to serve (this mode may be implemented also to a reflector in future). Also it is not
possible to change the receiver - once connected, the sender sends to the same receive/port
until stopped.

