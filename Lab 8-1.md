## Goal:
The goal of this lab was to learn how to do static routing with multiple networks in cisco packet tracer.

## Useful commands:
enable turns on the command line interface in the CLI tab of the router. config terminal turns on config mode. ip route (network address) (subnet mask) (Next router ip) adds a static route to the routing table to a network through the specified connected router on the same backbone network. show ip route shows a cli version of the routing table.

## Problems:
I had no problems with the lab.

## Question:
In order for you to create new static routes, you need a couple things. The first is the network address of the desired network. The second is the subnet mask of that network. The third is the ip of the next router on route to that network. after running the enable and config command, you run the ip route command with that information and that will setup the static routing information for that network. You do not need to do this for any network directly connected to the router.
