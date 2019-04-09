# PLC Communication
Packet Crafting with Python and Scapy. Communication between a Linux-based machine and the S7-1500 PLC.

Make sure you add the following rule in the firewall of the host where you are executing the Python Script. We want to avoid Reset packets coming out from the Linux machine. 

iptables -A OUTPUT -p tcp -d 192.168.0.1 -s 192.168.0.10 --dport 102 --tcp-flags RST RST -j DROP

-d. The IP address of the PLC.

-s. The IP address of your linux machine.

--dport. Port used by the PLC.

--tcp-flags. We want to drop any reset packet coming out from the Linux machine. 


The code inside the file S71500_U.py writes a value from the Analog Input Memory of the PLC (IW4). However it can be modified for writing in other spaces of memory.

The code inside the file S71500_U_R.py reads a value from the Analog Input Memory of the PLC. The example shows two different payloads for the IW4 and IW6 Memory.

The code inside the file S71500_D_R.py reads a value from the Digital Input/Output Memory of the PLC. The example contains two different payloads for the I1.0 and Q1.0 PLC memory. It should be noted that specific bits such as I1.3 or Q0.5 can't be addressed, instead the packet is composed by a byte that contains entire 8 positions.

The code inside the file S71500_D_w.py writes a value in the Digital Input/Output Memory of the PLC. The example contains two different payloads for the I0.2 and Q1.3 PLC memory. Same as above, the bit to modify should be addressed inside the byte of data at the end of the payload.  
