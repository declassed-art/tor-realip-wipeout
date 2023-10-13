# Tor patch: wipe out real IP received from peer

Did you know your Tor process receives your real IP address from the first Onion Router (OR) in the circuit?
This may look innocent, and I believe it's necessary for ORs to communicate with each other, but for Onion Proxy
which serves your TorBrowser this is highly dangerous, because the address is in memory and there's
a lot of SPECTRE class attacks out there we know about and much mode
zero day exploits we're not aware of yet which can pull it out.

You can dig into details yourself by studying the protocol in depth,
I'll just point you to `connection_or.c` which includes the following comment:
```
Send a NETINFO cell on *conn*, telling the other server
what we know about their address, our address, and the current time.
```

It's amazing, isn't it? Firewall won't help. VPN will, but...

Well, there's another place, where directory server returns X-Your-Address-Is in response headers.

The red pill is included.

You were warned.
