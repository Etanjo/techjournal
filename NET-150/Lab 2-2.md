## Goal:
In this lab we learned how to use ipconfig, and ping on linux while tracking the network activity through wireshark and learning how to extract information from there.

## Useful Commands:
The most useful commands we learned in this lab were ip route show, ping, and -c x. -c x limits the amount of pings your computer sends out where x is the number of pings. ip route show gives you all the network informartion of ipconfig/all, and ping pings.

## Problems:
The main problem I ran into in this lab was a slow vm, but I added more ram to it in the virtual box settings.

## Questions:
- A Mac address is a unique identifier of an object on a network. It is a 12 digit hexidecimal code that is split into two different pieces. The first half is the manufacturer's label, which is given to each device made by the same company.
The second half is a more specific number that only refers to that device withing the devices from that manufacturer. 

- You can find a mac address through commands like ipconfig/all and ip route show or through wireshark.
- Wireshark is aprogram that records network activities like requests and replies on your device while it is running so you can inspect the packets and get the desired information
- You can get a certain protocol in wireshark by searching for it in the packet list.
