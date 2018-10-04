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














































































































