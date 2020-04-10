# Sniffing Course on Pluralsight 
Link to the Course - 

# Module 1
## Several Attack Vectors

* Spoofing Attacks
* DHCP Attacks ```DHCP Starvation Attack , DHCP spoofing```
* Mac Flooding ```Switch is fed loads of ethernet Traffic```
* DNS Poisoning
* ARP Poisoning
* Password Sniffing
* Switch Port Stealing ``` when ARP poisoning is not possible ```


## Passive Vs Active Attacks

### Passive 
* Via a hub
* No packets are sent 
* Non Aggressive 
* Rarely used

### Active
* Influence the hardware
* Turning a Switch into Hub
* CAM - Content Addressable Memory
	* DHCP starvation
	* Mac Duplication
	* ARP spoofing
	* Mac Flooding 
	* *all of these techniques makes a switch go DUMB and act like  a normal HUB*

### Vulnerable Protocols

* HTTP 
* Telnet
* SNMP
* POP
* NNTP
* IMAP
* FTP
* rlogin

## Hardware Vs Software

* Hardware is very costly 
* Software is cheap ```Wireshark```
* OmniPeek
* Microsoft Network Monitor
* SoftPerfect NPA
* Airsnort
**Mobile Apps**
* Wicap2
* Packet Capture                                   


# Module 2 :- DHCP Assaults

```Against the assault of laughter,nothing can stand -Mark Twain ```

## What is DHCP ?

```
It is a Specialized server role (DHCP = Dynamic Host Conifguration Protocol). It provides IP address to each client connecting to the network automatically.It also provides other TCP/IP settings.
We automate the IP address allocation by giving a Dynamic IP to the client
DYNAMIC IP - It is where a computer gets an IP address from a DHCP server.It can change verytime the client reconnets to the Router.
In moden days the DHCP server is embedded inside the Router making it more convenient by using a automated firmware to configure it.
```
### The DORA process aka working of DHCP
```
The DHCP server assigns the IP to the Client and the steps followed is termed as DORA process.
DORA stands for -
D - Discover 
O - Offer
R - Request
A - Acknowledgement

DHCP Discover Message :- This is the first message which is sent by the DHCP client to discover DHCP Server in the network. This message is broadcast at Network and Data Link Layer.

DHCP Offer Message :- DHCP Offer Message is sent by the DHCP Server to DHCP client. In this message, DHCP Server offers an IP address to DHCP client. This message is unicast at Data Link Layer but broadcast at the network layer.

DHCP Request Message :- This message is sent from the DHCP client to the DHCP Server. In this message, DHCP client request to DHCP server for the offered IP address. This message is unicast at data link layer but broadcast at the network layer.

DHCP Acknowledgement Message :- This is the final message of DHCP DORA Process. This message is sent by the DHCP Server to the DHCP Client. This message is unicast at data link layer but broadcast at the network layer.
```

## DHCP Starvation Attack 

### Steps to performing this attack - 
1.**Step 1 - Starvation**  
	```We flood the nwtwork with dhcp dicover packets and make the dhcp server think the list of available IP's is full and no other client can connect to the server for sometime . 
	   This can be done using a tool on Kali called Yersinia```
2.**Step 2 - Going Rouge**
	```