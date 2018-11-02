# Networks

ARPANET -> 1982 (TCP/IP) --> WWW (1991)
IMP to work with gigmachine (Interfae message processor)
NCP -> Pcket switching (First made by ARPANET) to transmit data from devices
IMP -> Gatweays (1st router)

LAN - > liited connection (like computer clubs in old days)
WAN -> bigger LAN
MAN -> Metro city
Internetwork -> devices connected by routers
Internet -> worldwide internetwork TCP/IP for transfers with HTTP
Intranet -> internal internetwork only those who connected internally can connect to acess
Extranet -> allows limited # to external users

Mac -> is a device address attached to each PC, helps to identify where to send packets
Network interface -> card on motherboard to provide connection, and responsible for translation

The 7 layers:

1) Physical (4) -> converts bits into electrical impulses and signals
2) Data link (3) -> MAC address, NIC (network interface), local IP
3) Network (3) -> IP address, from who to who
4) Transport (2) -> data transfer, MTU (frame size, max trans unit), TCP, header, port numbers sequence
5) Session (1) -> Allows communication between devices before sending
6) Presentation (1) -> Data formatting, compression,from data to binary 01, encryption
7) App (1) -> data PDU

(1) The data itself
(2) Segragation into packets, sequaence, port number, transport headers(how to reassemble)
(3) To who (IP), from who, routing
(4)Identifies MAC address, ethernet locality

# NIC(2)
PHYSICAL LAYER (Layer 1=> physical)
START
2 Categories -> 1) wired, 2) wireless
- Bandwidth frequency -> how fast your connection is, amount of data transmitted, measured in hertz (Cycle per second)
- Network bandwith amount of data from 1 point to another, segment length, cable between devices

RJ45 connector -> Ethernet jack, so cable UTP or STP (unshileded) and (shileded)
When connecting PC the following concepts are used DTE and DCE (Data terminal/communication equipment) DCE more modern while DTE provides with terminal only.

FINISH


THIS IS LAYER 2 ( Data-link layer 2)

START
Switches, NIC -> Mac (48 bits, 12 hex -> 04-01-31-5B-1A-C4) the first 24 bits are for manufacturrer and the rest 24bit to device itself -> used for LAN
When connecting wirelessly NIC uses SSID (service set identifir) wireless usually 802.11ac or 802.11

- MAC is used to identify machines on the same network (layer 2)
- IP is used to identify machine through different networks (layer 3)
- NIC in this case works as an assembler of bits, electrical impulses into binary and vice versa. Additionally verifies MAC address, removes headers and sends result packets to network protocol (incoming). For (outgoing) recieves packets from network layer, creates frames headers with MAC and performs the conversion to bit.

Switch connects seeveral PC - network bridge -> requires no configuration, but if needs to be controlled remotely then needs manual conf. 1) Recieves a frame and reads MAC address and destintion. 2) Forwards frame to designated MAC and updats MAC tabe. 

FINISH

LAYER 3 (network layer 3)

START

Routes connects multiple networks, switches are oonly smart on layer 2, routers can connect LAN, WAN's etc together by utlising IP addresses.

So essentially switches work with MAC addresses, frames and switching tables, while routers work with IP, packets, routing table, broadcasts. These are the key differences between the 2.

FINISH

# Network Topologies

- Bus topology -> cannected straight up
- Star -> switch at the center, devices around
- Extended star -> switch and stars around
- Ring topology -> Man, metro, essentially circles of networks 
- Point to multi point -> a central point to comncate with everyone and responsible for granting permissions etc
- Mesh - same as PMP but has different routes, like blockchain, in case 1 breaks the connection is still up

- Ethernet protcol -> how data is send, LAN, based on 802.3 every station has MAC (48 bits, 12 hex)
- Ethernet frames -> Destination MAC, Source MAC, type data, FCS to check if its corrupted
- Ethernet media access -> rules when a devices can be access not to allow congestion.

# Routing

 - Static routing
 - Dynamic routing => 1) RIP, 2) OSPF
 
 Core components 
 - Adressing(IP)
 - Naming (DNS)
 - Routing (packets)
 
 Routing -> process of forwading packets from source to destination
 Routers -> network layer (layer 3), can be used to create internetowrk, (must have more than 2 interfaces (ports)
 
 Super netting - to reduce
 Sub netting - to increase
 
 (CISCO) Generic router!
 
 The communication netowkr with its nodes links is essentially weighted network graph
 
 Routers have:
 1) Physical
 2) Data link
 3) Network
 
 only 3 layers unlike a pc with 7
 
1) Physical
2) Data link
3) Network
4) Transport
5) Session
6) Presentation
7) App

Routing table
1) Destination network
CIDR notation as 172.16.0.0/16
2)Next hop
Interface name or the address of the next router in the path to the destinaton
3) Metric
Tells how far the destination, hop count
4) Timestamp
Tells when routing protocol updated the dynamic route

Types of tables
- Direct
Directly to router interface
-Remote network
No directly connected to the router, packet to another router to send
- Default routes
One route, go to default route

How to keep info in routing table
- Route summarisation
- Next hop
- Destination network
- Default route

Static routing
A network administrator builds it and maintains, predictable and simple, however doesnt scale and doesnt dynamically change networks. Only a few routers, ISP represents the only exit point.
If one of the routes is not defined in another router, then its send to default route
ADvantages: Easy, litle overhead, no extra CPU and memory
Disadvantge: if a link fails, have to manually reinstate
When to use: only a few routers, the ISP is the only exit point to internet, accessing a single default route.
 
Dynamic routing
Dynamic updating of tables, routing protocol, ability to recover from network faults.
IGP - interior gateway routing protocols -> for routing inside an autonomous system (AS), RIP, EIGRP, OSPF
EGP exterior -> routing between autonomous systemms, BGP
RIP = sends a copy of its routing table to all interface, each node keeps its own table and updates routing information.
Advantages: all topologies, automatically updates
Disadvantages: more complex to implement, CPU.

# ICMP ARTP TCP and UDP (7)

ARP - address resolution protocol (network layer)
IP - for network, MAC for machine delivery (network layer)

ARP is used to resolve a logical IP to MAC -> a sender broadcast requesting the hardware address of the destination, the destination responds unicast back to the source, telling it MAC. If address is cached then no need to send request, if no, then broadcast the requests. If local can be LAN requests if not the Router requests.   Sender and reciever caches addresses. To get MAC address it must be done locally.
Vulnurability: spoofing, posinoing. Can be done locally

ICMP (network layer)
reports errors, reports to original sender. Used by routers and hosts, performs query/reply for the internet protocol. If destination unreachable it notifies. If time exceeded TTL field reaches zero ICMP messages back to source and says the time exceeded. Query messages. Traceroute shows path a packet takes to reach its destination.  TTL is the amount of routers we have to pass through, for example PC A sends a packet to destination B, and there are 3 routers. If TTL = 1, then ICMP will send time exceeded in the first router, if TTL = 2 then on the second and so on. So to make it work u need to have TTL = 4 to reach the final destination with 3 routers. ICMP sends return information to sender
Vulnerability: DOS

# TCP/IP level 4 (transport)
Ensures the data is intact.  Reliable transfer. UDP small amount of data, lightweight (video). 
TCP segments the data. Helps to identify what application is running. To protect it they checksum, CRC (data integrity). Error control, integrity control. flow control (not overwhelm). TC Pconnection oriented protocol, BEFORE establishes (three way handshake) process with the destination then data is transfered. AFTER the connection is terminated by a fourway handshake. TCP offers full-duplex service -> data can be send concurrenty in both direction.

TCP headers
- 16 bits SOURCE
- 16 bits DESTINATION PORT (like nodejs listen.port, or react 8080 etc)
- 32 bits SEQUENCE NUMBER -> how to assembe in what sequence
- 32 bits ACKNOWLEDGMENT NUMBER -> tells that a specific data set recieved successfully, indicated that the next byte is expected from the other side of communication.
- 4 bit HLEN -> if urgent URG, RST - reset the connection, PSH,, ACK, SYN (initiate), FIN(finish)
- 6 bit RESERVER -> 
- 6 bit BITS field
- 16 bit WINDOW field - the size of the reciever buffer in bytes
- 16 bits Checksum - for integrity
- 16 bits POINTER -> flaglike HLEN

TCP starts connection -> 
3 way handsharke 
-> data transfer -> connection with a 4 way


# Application layer

App layer: http, smtp (simple mail), ftp(file transfer), ssh(tell net secure socket-shell), dhcp(dynamic host conf), dns. 

HTTP

WWW -> main concept is hyper text

Overview: u start a web browser and go to your website, web browser formats a request for home page by using app layer protocol http and goes down the chain of 7 OSI layers.
 URL - document on the internet (uniqe) (page)
  
SMTP
POP3 - post office protocol - download incomg messages from email servers to local area
IMAP4 - internet message access protocol - to manage email messages locally
SMTP - simple mail transfer protocol - sending email over the internet

MUA - mail user agent 
- email app
- to create, send , recieve etc messages
- to attach files

MTA - message transfer agent
- to prepare and transfer email messages

MIME - multio purpose internet mail extension
- to attach non-text based docs to emails


FTP
2 channels
1) to control commands port 20 (from server)
2) to transfer files port 21 (from client)
not secure

Based on TCP as well

SSH
Remote access (like ES2 aws instance can be accessed through ssh) 
telnet - port 23
ssh - port 22

DHCP (dynamic host conf protocol)
Keeps IP addreses to hosts, if one pc is shut down it assigns IP to another computer, hence dynamic.On UDP port 67 for IP address requests.
DHCP server is composed of
- IP address scope - range of IPs server can lease to clients
- scope options - IP settings, DNS
- reservation - IP to particular MAC address
- exclusion - a certain number of IP's to be excluded from scope

Only for a certain period of time, when it reaches 50% time elapsed it asks if same IP can be used, if no response then its ok. Around 87.5 time expired it asks again, if no answer then uses it till the ened and eventually broadcasts dchp for new IP address.

Broadcast Logic: 
- DHCPDISCOVER - the client announces its search for DHCP server
- DHCPOFFER - the server replies and offers an IP for lease
- DHCPREQUEST - the client express the desire to use  IP
- DHCPACK - the server acknowledges it and allows to to use IP

DNS
Names to IP adresses like 192.168.0.1 - www.welcome.org
each .org .com. .com.au .gov etc have their own databases
Uses UDP because its usually consists of a single pack
- TLD - top level .com .org. .gov
- SLD - second level .edu etc
- Subdomain - is optional 

DNS zone - difference spaces within a global DNS
DNS zone file - representation of dzone
Resource record - the data contained in the zone
DNS cache - cache of DNS names
ROOT hints - file containing of all IP address
DNS - server service listens for DNS queries on UDP port 53
Vulnurabilites:
- The basic DNS scheme is insecure
- Cache poising attack - redirects to other website
- Data interception/traffic diversion
- Man in the middle
- DOS

DNSSEC
Same as DNS but far more secure, it was  its initial goal.
- If responds came from legit DNS source
- Data integriy - checks if data was modified
- Auth denial of existence






# IPv6
IANA 5 regional, 
- APRAN -america, 
- LACCNC-latin, 
- RIPE NCC - EU, RUSSIA, Middle east, 
- AfrNIC - Africa,
- APRNC-asia


Router performs fragmentation but in IPv6 no. 

2^32 - 4.3 billion IP addresses for IPv4
NAT - all trafic leaving lan appears as originating from global IP address, behind it can use private IP addresses. NAT works as the routing mechanism, like nginx.
NAT - cannot be used with IPSec in transport mode
NAT 0 is not a firewall
NAT - breaks the end to end communcations
Plus - binding time out
Shortage of IPv4 limits internet growth

IPv4 and IPv6 header differences,
Total length is gone, fragmentation is gone, checksum is gone 

IPv6 2^128
FEDC:BA45:1234:3245:E54E:A101:1234:ABCD
/60 (indicate the bits for network portion)
is hexadecimal not in binary like 1090::9:900:210D:325F/60 where (::) represents zero

DHCPv4 enables servers to allocate IP adresses to hosts that join the network
In IPv6 the host will configure itself with IP without server, eliminating manual IP config, and dynamic renumbering (changing ISP's etc)

QoS
- protcols can provide different data streams with priorities with high quality, bandwtih and delay times
- two field in IPv6 can be used for QoS - traffic class, the flow label.

 
Built in support for IP secutrity unlike ipv4
- uses extension headers for security provisioning
- Auth header (AH) auth and integriy
- Encapsulating security payload ESP (integrity and confidentiality)

Mobility support
- An IP adress is bound tighly to the network where the device is
- Allows to have 2 IP addresses, a primary (home wifi) and secondary IP within the foreign network.

Co-existence 

# Internet of things (IoT) cloud computing

global infrastructure for the information society enabling advanced tech

SMIGHT BASE ( like a base for tech things)
- public wifi
- emergency call
- envrionment sensors
- charging pooints
- traffic and parking managment into street lighting


Example of long/short range tech
Lora 2 surban, 15 surban, 45km rural
Sub-ghz
ISM - yes
date rate: 0.3 -27kbps
Power consumption: low

1)Sigfox 10-50km, 868/902 mgz
2) zigBee 100m

Assembly
hardware
- micro controller
- transiever
- actuators/sensors
- power source

LORA
-  components
controller - arduino
transiever - SX1276
Sensors
Power supply
- Gateway interface
lora network SX1301
internet IP based
- Network Server
network application server
 

LORA arhitecture
Network design
- HW selection
- Gateway placement
- Security

Network managment
- Network performance dependencies
- power consumption
- firmware and soft updated
- security
- scalability
- compatability

Sass
Everything is supplied by the provider

PAAS
Install applicaition urself, software system and computer hardware is supplied

IASS
App and system software should be installed by yourself



# Cyber security
 zero-day-exploit - taking advantage of undiscovered software vulnurebilitiy, most of which are generally known

Risk in association with people
- human errors, ignorance, omissions
- social engineering - phishing to be a pretender

Risk associated with transmission and hardware
- man in the middle
- eavesdropping -listening
- sniffing - repeatig devices brocast traffic
- port acess via port scanner - unused port are not secured
- router attack - router not configured to drop suspicious packets

Risk with protocols and software
- Transport, session, presentation and application layers
- TCP/ip flaws
- Invalid trust relationshops
- NOS back doors
- buffer overflow
- administrators default security opt
- intercepting transactions between applications

Risk with internet access
- network sec compromise (from inside
- outside threats
- common internet related issues (FTP), imporper conf firewall, DOS

Security policies
- privacy
- authentication
- internet use
- acess
- auditing
- data protection

If something happens then a response policy should be in place
- security breach occurence
- response team members
- after problem resolution


Vulnurabilities
- IP fragmeneted packet attacks
- ARP cache posioning man in the middle
- ICMP ping of death attack
- TCP syn flood attack (handshake)
- DNS dns cache poisining (redirect users to another website)


















