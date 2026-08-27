## Goal:
The goal of this lab was to use packet tracer in order to understand how exactly RIPv2 dynamic routing works, and how to set it up on the routers

## Useful Instructions:
The most useful instructions were how to set up RIPv2 and how to hide certain event types. In order to setup RIPv2, you need to go into the router config menu (enable, config terminal) and type in router rip. Then type version 2, and then type network x (where x is the ip of the network directly connected to the router.) if you exit config mode, you can type show ip route to see the routing table on the router. When changing what can be seen in the event list, you can edit the filters. It is often easier to hit the show all/none button to turn everything off before enabling specifically the filters you want

## Problems:
I had trouble finding the RIP requests in the event list, and I did not know how to see the types. If you expand the event list window, you can see the types of requests

## Questions:
Setting up RIPv2 is included in Useful Instructions.
I did not have problems that required much troubleshooting, methods are included in problems (and some in instructions).
