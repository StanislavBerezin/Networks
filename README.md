# Specs
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
PHYSICAL LAYER (Layer 1-> physical)
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














































































































