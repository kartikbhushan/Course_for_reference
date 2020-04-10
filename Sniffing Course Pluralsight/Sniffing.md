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

1.**Passive** 
* Via a hub
* No packets are sent 
* Non Aggressive 
* Rarely used

2.**Active**
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
## The DORA process aka working of DHCP

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
```
We flood the nwtwork with dhcp dicover packets and make the dhcp server think the list of available IP's is full and no other client can connect to the server for sometime . This can be done using a tool on Kali called Yersinia
```

2.**Step 2 - Going Rouge**
```
In this step we wil set up a fake DHCP server. For this we need to starve the original DHCP server making it go offline. 
We now introduce our rouge server on the server and packets automatically redirect to the fake server since the original sever is sitting offline.
Once we receive the DHCP dicover packets the rouge server can issue IP and attacking DNS ip address to the client which could have a fake website (Bank login page,Amazon,..... :)).
It is very difficult to detect on the network.
```

### Countermeasures to prevent these attacks.

1.**Enabling Port Security**
```It is designed to set maximum number of Mac Addresses per port.```

2.**DHCP snooping**
```Stops ports from responding to DHCOOffers```


# Module 3 :- Big-MAC Attacks 

```Sometimes you need to take what is rightfully yours .This is why I see the hand burglar as a hero - Frank Underwood```

## What is a MAC ?

```
MAC- Media Access Control
MAC address is responsible for sending and receiving of the packets and not the IP
MAC address is a 12 digit number it is also called as Physical Address
First 6 are the prefix to specific vendors.
ff-ff-ff-ff-ff-ff is a unique address and is refered to as the broadcast address and addresses ever adapter in the network itself .
```

## MAC in reverse is CAM

```
CAM - Content Addressable Memory
Content Addressable Memory (CAM) table is a system memory construct used by Ethernet switch logic which stores information such as MAC addresses available on physical ports with their associated VLAN Parameters. The CAM table, or content addressable memory table, is present in all switches for layer 2 switching. This allows switches to facilitate communications between connected stations at high speed and in full-duplex regardless of how many devices are connected to the switch.

Switches need to keep track of the MAC addresses of all connected devices. Without the learning function, the switch would not know to which port the destination device is connected. At the center of the learning function is a part of the switch’s memory. We refer to this memory location as the MAC Address Table. As the switch receives a data packet, it reads the source address and maps the port number to the MAC address in that source field
```

## Flooding 

```
MAC flooding is a technique employed to compromise the security of network switches. The attack works by forcing legitimate MAC table contents out of the switch and forcing a unicast flooding behavior potentially sending sensitive information to portions of the network where it is not normally intended to go.

When we flood the CAM tables of the switch , The switch doesnt know how to handle all the traffic together andto avoid packte loss or connection loss it reverts back to acting like a HUB, , flooding is when a switch pretends to be a hub.
```

## Countermeasures to prevent MAC attacks.

1.**Port Security**
```Secure MAC ==> Secure Port```

2.**AAA Servers**
```
AAA server (authentication, authorization, and accounting)
They require users and computer to authenticate themselves and tracks where they are going and what they are doing on the Network.
```

# Module 4 - ARP Poisoning  

```You can only trick people for so long ... but until then take advantage the situation```

## What is ARP 

```
ARP - Address Resolution Protocol. It resolves the MAC address to an IP address
ARP cache is stored in memory and can be manipulated very easily.
```

## ARP spoofing 

```
ARP spoofing is a type of attack in which a malicious actor sends falsified ARP (Address Resolution Protocol) messages over a local area network. This results in the linking of an attacker’s MAC address with the IP address of a legitimate computer or server on the network. Once the attacker’s MAC address is connected to an authentic IP address, the attacker will begin receiving any data that is intended for that IP address. ARP spoofing can enable malicious parties to intercept, modify or even stop data in-transit. ARP spoofing attacks can only occur on local area networks that utilize the Address Resolution Protocol

MITM attacks

Client -------------------------------------------------------------> Router
(IP-192.168.1.42, MAC-22-22-22-22-22-22)                             (IP-192.168.1.1, MAC-11-11-11-11-11-11)

Hacker (IP- 192.168.1.69, MAC-33-33-33-33-33-33) ----> wants to get in middle of the connection of the client and the router 

Now the hacker will achieve this in two steps 
1.Tell the client that he is the Router 
2.Tell the Router that he is the Client


So STEP 1:- Hacker associates routers IP with His MAC to the client (ROUTER_IP ---> HACKER_MAC)
Hacker -------------------------------------------------------------> Client
(IP-192.168.1.1, MAC-33-33-33-33-33-33)                             (IP-192.168.1.42, MAC-22-22-22-22-22-22)

STEP 2:-Hacker associates Clients IP with His MAC to the router (CLIENT_IP -----> Hacker_MAC)
Hacker -------------------------------------------------------------> Router
(IP-192.168.1.42, MAC-33-33-33-33-33-33)                             (IP-192.168.1.1, MAC-11-11-11-11-11-11)


So finally its looks like :
Client <------------------------------->Hacker<----------------------------->Router

Now the hacker is in middle of the connection and can sniff all the traffic flowing through the client without client even noticing it .

```

## Dangers Of ARP Attacks

* DOS
* Packet Sniffing
* VoIP Tapping
* MITM
* Session Hijacking (Passive/Active)
* Data Interception
* Connection Hijacking
* Data Manipulation (Very Dangerous)
* Steal Passwords
* Connection Resetting

## Countermeasures of ARP attacks

1.**Dynamic ARP Inspection (DAI)**
```Timely checks to see if a ARP packet is Valid if not then they are dropped ```

2.**Static ARP Tables**

3.**ARPWatch**
```Notes down the ARP tables at the start of the connection and notifies the ADMIN if there is any change later or in middle of a connection time```

# Module 5 - DNS Poisoning

```We have nothing to fear ... but an attacker with your DNS Cache! - I.V. Ben Pwned```

## What is DNS 

```
DNS- Domain Name System
The Domain Name System (DNS) is the phonebook of the Internet. Humans access information online through domain names, like nytimes.com or espn.com. Web browsers interact through Internet Protocol (IP) addresses. DNS translates domain names to IP addresses so browsers can load Internet resources.

Each device connected to the Internet has a unique IP address which other machines use to find the device. DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4), or more complex newer alphanumeric IP addresses such as 2400:cb00:2048:1::c629:d7a2 (in IPv6).
```
## How DNS work

```
The process of DNS resolution involves converting a hostname (such as www.example.com) into a computer-friendly IP address (such as 192.168.1.1). An IP address is given to each device on the Internet, and that address is necessary to find the appropriate Internet device - like a street address is used to find a particular home. When a user wants to load a webpage, a translation must occur between what a user types into their web browser (example.com) and the machine-friendly address necessary to locate the example.com webpage.

In order to understand the process behind the DNS resolution, it’s important to learn about the different hardware components a DNS query must pass between. For the web browser, the DNS lookup occurs “ behind the scenes” and requires no interaction from the user’s computer apart from the initial request.

There are 4 DNS servers involved in loading a webpage:
1.DNS recursor - The recursor can be thought of as a librarian who is asked to go find a particular book somewhere in a library. The DNS recursor is a server designed to receive queries from client machines through applications such as web browsers. Typically the recursor is then responsible for making additional requests in order to satisfy the client’s DNS query.

2.Root nameserver - The root server is the first step in translating (resolving) human readable host names into IP addresses. It can be thought of like an index in a library that points to different racks of books - typically it serves as a reference to other more specific locations.

3.TLD nameserver - The top level domain server (TLD) can be thought of as a specific rack of books in a library. This nameserver is the next step in the search for a specific IP address, and it hosts the last portion of a hostname (In example.com, the TLD server is “com”).

4.Authoritative nameserver - This final nameserver can be thought of as a dictionary on a rack of books, in which a specific name can be translated into its definition. The authoritative nameserver is the last stop in the nameserver query. If the authoritative name server has access to the requested record, it will return the IP address for the requested hostname back to the DNS Recursor (the librarian) that made the initial request.
```

## Intranet Poisoning / Internet Poisoning

```
Once you perform the ARP spoofing attack on a client you can then look at the sites they are requesting and then respond to them with the IP of the phising site you want .
```
## Proxy Server Poisoning

```
Attacker sends a piece of malware to change browser settings of the clients browser to redirect to hackers proxy server.Once hacker achieves this then he can sniff all  the clients traffic flowing through his proxy server.
```

## DNS Cache Poisoning

```
Very difficult now . Not very possible. 
Cause the Cache now lies with the ISP or if locally on your local machine then we need a malware to inject and change entries but getting in the malware is very difficult in real life. :)
```

# Module 6 - CounterMeasures 

```Your job isn't to " STOP THEM " . Your job is to slow them down - SuperDale```

## Detecting Sniffers via ARP

```
1.Non-broadcast ARP packet 
2.Ping the IP with wrong MAC address.
3.Machine in Non promiscuous Mode will respond with a ARP request saying that your MAC was this and not this one.
4.Machine in promiscuous mode will respond without checking the MAC to the Ping and hence is "CAUGHT".
```

## Detecting Sniffers via DNS

```
Read Google for this.
```
## Protection

* Encryption
* Static MAC of Gateways
* Physical Access
* Upgrade to IPv6
* Switch off network ID broadcast
* Static IP's
* Static ARP entries
* HTTPS
* SFTP
* VPNs/IPsec
* SSL/TLS
* Wireless Security(WPA2/WPS)
* Direct MAC retrieval


# ------------------------------------------------------------THE END ----------------------------------------------------------
