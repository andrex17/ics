# PLC Communication
This repository allows you to craft packets and communicate with the S7-1500 PLC.

Make sure you add the following rule in the firewall of the host where you are executing the Python Script. We want to avoid Reset packets coming out from our linux machine. 

iptables -A OUTPUT -p tcp -d 192.168.0.1 -s 192.168.0.10 --dport 102 --tcp-flags RST RST -j DROP

-d. The IP address of the PLC.

-s. The IP address of your linux machine.

--dport. Port used by the PLC.

--tcp-flags. We want to drop any reset packet coming out from our linux machine. 
