## Goal:
The goal of this lab was to use wireshark to observe how tracert works.

## Useful Commands: 
Tracert

## Problems:
I ran into no problems.

## Questions: 
Traceroute works by attaching a ttl number to the packet it sends out. This TTL number causes that router in the sequence to discard the request, and send a messange back to the source. The TTL then increases, and repeats for the next router. This continues until the packet reaches the destination.
