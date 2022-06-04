# The Networking 101 GCP sheet

It's easy to get lost in a conversation around networking. I hope this referrence sheet can help with that.  

This is a quick 101 level reference guide of general networking terms and Google Cloud networking specific services.  

By the Developer Relations Engineer Ammett Williams of the Google Developer Relations Team.  

<img border="0" valign="middle" src="img/net101.gif">  

[Download pdf version : ](pdf/network101gcp.pdf)

[**PDF**](pdf/network101gcp.pdf)

For more about Google Cloud services check out the [Interactive Google Cloud Developer's Cheat Sheet](https://goo.gle/GCdevelopercheatsheet) 

----------------------------
# Contents
<sup>:link: - Link icon</sup>

### Global Network I & II


* **Network**: Is a collection of connected devices for the purpose of communication. This can be a physical or logical connection. 
* **Fiber Optic Cable**: Cable made up of optical pairs that transmit data using light. 
* **Internet**: Public network of networks which exchanges routes through BGP.
* **Region**: A Google Cloud geographic compute location (Made up of minimum 3 zones). [<sup>:link:</sup>](https://cloud.google.com/compute/docs/regions-zones#identifying_a_region_or_zone) 
* **Zone**: Google Cloud compute facility within a region. [<sup>:link:</sup>](https://cloud.google.com/compute/docs/regions-zones#identifying_a_region_or_zone) 
* **Point of presence (PoP)**: A connection point from the internet to Google’s network. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/edge-locations) 
* **On-premise**: Data center belonging to an enterprise. 
* **Local Area Network (LAN)**: This is a network that shares same communication lines in a distinct geographic area.
* **Virtual LAN (VLAN)**: A logical method to allow communication between systems that are located on different LAN segments.


### VPCs and IP addressing
  
* **Virtual Private Cloud (VPC)**: A VPC is a Logical representation of an on-prem network. This is a global construct in GCP. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/vpc) 
* **VPC modes**: These are two modes auto mode and custom mode, available in GCP. [<sup>:link:</sup> Auto mode](https://cloud.google.com/vpc/docs/vpc#subnet-ranges) [<sup>:link:</sup> Custom mode](https://cloud.google.com/vpc/docs/vpc#subnet-ranges)
* **VPC subnets**: These are regional and assigned to an IP address range. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/subnets) 
* **IP address**: A unique address used to identity host on network. Made up of network and host portions. [<sup>:link:</sup>](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html#anc5) 
* **Subnet mask**: This segments and IP address into network and host portions.  [<sup>:link:</sup>](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html#anc13) 
* **IPV4**: This is a 32 bit, 4 octet address. Written in binary or dotted decimal format. E.g. 192.168.10.20 or 11000000.10101000.00001010.00010100
* **IPV6**: This is a 128 bit, hexadecimal address. 2001:DB8:7654:3210:FEDC:BA98:764:3203
* **Private IP (RFC1918)**: A special range that can be used internally by anyone. These are non internet routable. [<sup>:link:</sup>](https://datatracker.ietf.org/doc/html/rfc1918) 
* **Public IP**: IP address that is routable on the internet  
* **DHCP**: Dynamic Host Control protocol. A method to automatically assign an IP address to a client. [<sup>:link:</sup>](https://wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol) 
* **Static IP**: An IP that does not change after being assigned. 
* **Ephemeral IP**: Temporary IP that is not reserved/static.  
* **Bring Your Own IP (BYOIP)**: Use external IP addresses that you own in Google Cloud  [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/using-bring-your-own-ip)
* **Alias IP**: Additional addresses that can be assigned to your VM, these can be taken from the primary or secondary address range. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/alias-ip) 
* **Secondary IP**: Secondary range of IP address that can be assigned to your VM in GCP. 
* **Restricted.googleapis.com IP**: Used to access external GCP APIs via google private network. 199.36.153.4/30. Used when VPC service controls are enabled and you need to access only VPC service control supported APIs. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/configure-private-google-access) 
* **Private.googleapis.com IP**: Used to access external GCP APIs via google private network. 199.36.153.8/30 [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/configure-private-google-access) 
    
### OSI model and Internet model
  
* **What is the OSI model**: A 7 layer conceptual model that provides interoperability of the TCP stack. [<sup>:link:</sup>](https://learningnetwork.cisco.com/s/article/osi-model-reference-chart) 
* **Application layer (layer 7)**: User interface and application. Protocols examples HTTP, HTML
* **Presentation layer (layer 6)**: Formats data to be presented. Protocols examples JPEG, ASCII, GIF 
* **Session layer (layer 5)**: Creates, tracks, ends the sessions between different systems. 
* **Transport layer (layer 4)**: Handles message delivery using connection and connectionless protocols. Protocol examples TCP, UDP.  
* **Network layer (layer 3)**: Focuses on subnets, route path selection. Protocols examples IP, ICMP,. Router work here.
* **Data layer (layer 2)**: Focuses of transferring data frames over physical layer. Protocol, ARP, PPP, VLANS. Switches work here.
* **Physical layer (layer 1)**: Transmission of raw bits over physical mediums. Examples network cables, wireless 
----
* **What is the internet model**: A 4 layer model conceptual model of the TCP/IP  stack.   
* **Application layer**: User interface and application. 
* **Transport layer**: Responsible for end to end data handling of data streams
* **Internet layer**: Responsible for routing packets through networks.  
* **Link layer**: From a device it interacts with physical network. 

### TCP, TCP three-way handshake, UDP, QUIC
  
* **Transmission Control Protocol (TCP)**: This is a connection oriented protocol that handles reliability, flow and congestion control of packets. It establishes a connection before sending a packet. [<sup>:link:</sup>](https://datatracker.ietf.org/doc/html/rfc793) 
* **Transmission Control Block**: Contains all the information about the connection and implements the sliding window.
* **Sliding window**: Determines the amount of bytes that one system can send to the other. Once these byes are received by the receiver, the sender sends another set of bytes is sent until all data is sent.
* **Three-way handshake**: This is the sequence to form a TCP connection. It involve the SYN, SYN/ACK, ACK flag exchange between client/server. 
* **Flag**: These indicate the state of the connection. 
* **SYN**: The SYN or synchronize flag is sent to start the TCP connection process.
* **ACK**: The ACK or the acknowledgement flag. This confirms that data was received. 
* **FIN**: A flag sent to request termination of connection.
* **User Datagram Protocol (UDP)**: This is a best effort delivery protocol.  
* **Quick UDP Internet Connections (QUIC)**: A Google made transport layer protocol. This is built on top of UDP.[<sup>:link:</sup>](https://peering.google.com/#/learn-more/quic) 
* **Transport Layer Security (TLS)**: A protocol that provides cryptography by using certificates. [<sup>:link:</sup>](https://en.wikipedia.org/wiki/Transport_Layer_Security) 

### Packet, Frame, MTU
  
* **Data messages types**: These are frames, packets, datagrams. They may exist at different layers of the OSI model.
* **Maximum transfer unit (MTU)**: The size of the largest unit of data that can be transmitted over the network.
* **Time to Live (TTL)**: This indicates the life of the packet usually has a max of 255 hops. This ensures packets don’t exist forever in a network.  
* **Unicast message**: These are sent on a 1 to 1 basis on a network.  
* **Multicast message**: These are sent to subscribed groups on a network. 
* **Broadcast message**: These are sent to every device on a network.  
 

### ARP, RARP, DNS & NAT
  
* **Domain Name Service (DNS)**: Resolves names to IP addresses.
* **Cloud DNS**: Google Cloud managed DNS offering. [<sup>:link:</sup>](https://cloud.google.com/dns/docs/overview/) 
* **Internal DNS**: Used internally within a private network. 
* **DNS Security Extensions (DNSSEC)**: Uses digital signature to secure DNS information. [<sup>:link:</sup>](https://cloud.google.com/dns/docs/dnssec)  
* **Hybrid DNS**: DNS configured between cloud and on-prem or external networks. For GCP examples click link. [<sup>:link:</sup>](https://cloud.google.com/dns/docs/best-practices#choose_where_dns_resolution_is_performed)  
* **Address resolution Protocol (ARP)**: Protocol used to resolve IP address to a MAC/link layer address. Maintained in the ARP table. [<sup>:link:</sup>](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_arp/configuration/15-s/arp-15-s-book/Configuring-Address-Resolution-Protocol.html#GUID-A7E9469A-187E-4811-BB1F-5013E13E1B6B) 
* **Reverse ARP (RARP)**: This is the inverse of ARP. Used to resolve MAC to IP addresses.
* **Media Access Control address (MAC)**: Unique hexadecimal identifier assigned to a network interface controller (NIC) card. Usually a 12 digit hexadecimal number.  [<sup>:link:</sup>](https://en.wikipedia.org/wiki/MAC_address)  
* **Network Address Translation (NAT)**: Allows private IP ranges to communicate with the internet. Maintains a NAT table of private to public address & port mappings for communications. 
* **Cloud NAT**: Google Cloud managed NAT service [<sup>:link:</sup>](https://cloud.google.com/nat/docs/overview)  

### Routing, Cloud Router, Dynamic Routing, BGP, MPLS
  
* **Routing**: Selecting a path for traffic to flow within internal networks or between different networks.
* **Router**: Allows communication between different networks.  
* **Cloud Router**: Google Cloud router that allows you to dynamically exchange routes between your VPC and on-prem using BGP. [<sup>:link:</sup>](https://cloud.google.com/network-connectivity/docs/router/concepts/overview)  
* **Routing table**: A repository of all the routing information within a network. 
* **Routing modes**: These are [static](https://en.wikipedia.org/wiki/Static_routing) or [dynamic](https://en.wikipedia.org/wiki/Dynamic_routing). 
* **Static routing**: These routes  are fixed an don’t update. They usually have to be manually adjusted.
* **Dynamic routing**: These routes update  to reflect current state. 
* **Route summarization**: Used to reduce the number of route advertised to neighbours. See example. [<sup>:link:</sup>](https://www.ciscopress.com/articles/article.asp?p=2995352)  
* **next-hop**: The address of the next router in the transit route of a packet. 
* **Software Defined networking**: A software based networking approach that uses application programming interfaces (API) to communicate with underlying infrastructure to control the network traffic. [<sup>:link:</sup>](https://en.wikipedia.org/wiki/Software-defined_networking)  
* **Border Gateway Protocol (BGP)**: Is the path vector protocol of the internet. Made up of Autonomous systems (AS) uses TCP port 179.  [<sup>:link:</sup>](https://datatracker.ietf.org/doc/html/rfc4271)  
* **Autonomous System (AS)**: Is a collection of connected Internet Protocol (IP) routing prefixes under the control of one or more network operators.  
* **Autonomous System Number (ASN)**: A repository of all the routing information within a network. 
* **External BGP (eBGP)**: BGP connection formed between different AS’s. 
* **Internal BGP (iBGP)**: Connection formed within the same AS.
* **Multiple Exit Discriminator (MED)**: This is one of several BGP attributes used to influence path selection. This is non transitive and the lower metric wins.  [<sup>:link:</sup>](https://datatracker.ietf.org/doc/html/rfc4271#section-5.1.4)  
* **AS-path prepend**: This is one of several BGP attributes used to influence path selection. This is a mandatory attribute. The shorter path should be preferred.[<sup>:link:</sup>](https://datatracker.ietf.org/doc/html/rfc4271#section-5.1.2)  
* **Multiprotocol label switching (MPLS)**: This is a switching method that uses labels instead of IP information to transmit packets across the backbone core at high speed. 
* **Bidirectional Forwarding Detection (BFD)**: This is a protocol that detects failure quickly on links when enabled. In GCP you can use this [feature](https://cloud.google.com/network-connectivity/docs/router/concepts/bfd) with Cloud Router. 

### Connectivity and Hybrid connectivity
  
* **Dedicated Interconnect**: Dedicated connection between Google and your private network. Available from 10 GBit/s to 100 GBit/s. Has high availability configuration and you can use multiple links. [<sup>:link:</sup>](https://cloud.google.com/network-connectivity/docs/interconnect/concepts/dedicated-overview)
* **Partner Interconnect**: Highly available connection between Google and your network provisioned through a Service Provider. Available from 50 MBit/s to 10 GBit/s. Has high availability configuration and you can use multiple links. [<sup>:link:</sup>](https://cloud.google.com/network-connectivity/docs/interconnect/concepts/partner-overview)  
* **Virtual private network (VPN)**: This offers a secure connection between two locations over a secure IPSEC tunnel. 
* **Cloud VPN**: Google Cloud VPN service. [<sup>:link:</sup>](https://cloud.google.com/network-connectivity/docs/vpn/concepts/overview)
* **Carrier Peering**: Google Cloud service that enables you to access Google Workspace and other Google apps via service provider connection.  [<sup>:link:</sup>](https://cloud.google.com/network-connectivity/docs/carrier-peering)
* **Direct Peering**: Google Cloud service that enable you to access google Workspace and other Google apps via direct connection to Google edge.  [<sup>:link:</sup>](https://cloud.google.com/network-connectivity/docs/direct-peering)
* **Shared VPC**: GCP service that allow you to provision and connect host projects, and service projects. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/shared-vpc)
* **VPC Network Peering**: GCP service that allow you to connect between different VPC’s in the same or separate project and organizations. This is 1-to-1 peering that is not transitive. Max peering per VPC is 25 connections.  [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/vpc-peering)
* **Traffic Director**: Google Cloud service that offers a fully managed traffic control plane for service mesh. [<sup>:link:</sup>](https://cloud.google.com/traffic-director/docs/features)

### Network Security
  
* **Firewalls**: Allow, deny & filter traffic based on rules. Affect ingress and egress traffic.
* **Firewall rules**: Criteria used to deny, allow access in GCP e.g. IP, source, tag, service account. [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/firewalls)  
* **Distributed denial of service (DDoS)**: This is a type of attack that affect availability of service by overloading the systems. [<sup>:link:</sup>](https://en.wikipedia.org/wiki/Denial-of-service_attack) 
* **Cloud Armor**: Google Cloud service that provides filtering at OSI layer 7 to 4.  [<sup>:link:</sup>](https://cloud.google.com/armor)
* **VPC Service Controls**: Google Cloud service that allows you the ability to create  perimeters that protect resources and data.  [<sup>:link:</sup>](https://cloud.google.com/vpc-service-controls/docs/overview?hl=en)
* **Cloud Identity-Aware Proxy (IAP)**: Google Cloud service that controls access to your application  and restricts it to only authorized users.  [<sup>:link:</sup>](https://cloud.google.com/iap/docs/concepts-overview)
* **Security Command Center**: Google Cloud service that has asset discovery, threat detection, and threat prevention components. [<sup>:link:</sup>](https://cloud.google.com/security-command-center/docs/concepts-security-command-center-overview)
* **Beyond Corp**: Google Cloud [zero trust](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/44860.pdf) model.  [<sup>:link:</sup>](https://cloud.google.com/beyondcorp-enterprise/docs/overview)


### Traffic handling, Load balancing, Content Delivery
  
* **HTTP(S) Load Balancer**: Global load balancer for HTTP(S) traffic. [<sup>:link:</sup>](https://cloud.google.com/load-balancing/docs/https)
* **SSL proxy**: Global load balancer for SSL traffic. [<sup>:link:</sup>](https://cloud.google.com/load-balancing/docs/ssl)  
* **TCP proxy**: Global load balancer for TCP traffic. [<sup>:link:</sup>](https://cloud.google.com/load-balancing/docs/tcp) 
* **Network LB**: Regional LB used to load balance TCP traffic (available internally and externally).  [<sup>:link:</sup>](https://cloud.google.com/load-balancing/docs/network)
* **Internal LB**: Regional LB used with a VPC.  [<sup>:link:</sup>](https://cloud.google.com/load-balancing/docs/internal)
* **Network Endpoint Group (NEG)**: Network Endpoint Group are used to attach a backend pool to a load balancing service in Google Kubernets Engine (GKE).  [<sup>:link:</sup>](https://cloud.google.com/load-balancing/docs/negs)
* **Ingress**: Allows HTTP(S) traffic connections to a Kubernetes cluster. [<sup>:link:</sup>](https://kubernetes.io/docs/concepts/services-networking/ingress/)
* **Content Delivery Network (CDN)**: Caches content at a distribution endpoint closest to customer.

* **Cloud CDN**: Google Cloud standard CDN offering.  [<sup>:link:</sup>](https://cloud.google.com/cdn/docs/overview)
* **Hyper Text Transfer Protocol (HTTP)**: Protocol used for transmitting hypermedia documents. This is a standard on the internet, more commonly in it secure form HTTP(S).  [<sup>:link:</sup>](https://developer.mozilla.org/en-US/docs/Web/HTTP)
* **HTTPS**: Secure version of HTTP enabled by using TLS on the connection. [<sup>:link:</sup>](https://en.wikipedia.org/wiki/HTTPS)

### Troubleshooting & Monitoring
  
* **ping**: This tool checks the availability of host by using Internet Control Message Protocol.
* **Traceroute or tracert**: Shows the hops between source and destination. 
* **nslookup**: Allows you to resolve IP from host name. 
* **Domain information groper (dig)**: Performs DNS lookup and displays the answers of the query.
* **ipconfig or ifconfig**: Show the IP address, subnet and gateway information of a system.
* **Flow logs**: This GCP service tells you about the traffic flow in your VPC.  [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/flow-logs)
* **Network Intelligence Center**: GCP service that provides you with a few tools to gain visibility into your network. [<sup>:link:</sup>](https://cloud.google.com/network-intelligence-center)
* **Audit Logs**: Google Cloud logs that provide information on activities in your cloud. A few are; Admin Activity, Data Access, system events and Policy denied, audit logs. [<sup>:link:</sup>](https://cloud.google.com/logging/docs/audit)
* **Cloud Operations**: Google Cloud tool that allows you to monitor, log and trace application and systems in your environments. [<sup>:link:</sup>](https://cloud.google.com/products/operations)
* **Packet Mirroring**: Packet Mirroring clones the traffic on the network and forwards it for examination. See more [<sup>:link:</sup>](https://cloud.google.com/vpc/docs/packet-mirroring)
* **Service Directory**: A GCP  managed service that gives you a single place to publish, discover, and connect services. See more [<sup>:link:</sup>](https://cloud.google.com/service-directory/docs/overview)


### What happens when you type www.google.com in a browser

 - 1 - Open browser type www.google.com  
- 2 - Browser cache is checked to see if IP information was cached  
- 3 - If #2 has no info, system checks host file for address information
- 4 - If #3 has no info, system queries local DNS
- 5 - If #4 has no info, query is sent to Service Provider (SP) DNS
- 6 - If SP has no info, query sent to Root level DNS
- 7 - Root level returns the Top level DNS
- 8 - Top level DNs returns the Authoritative DNS who has the record  
- 9 - Authoritative DNS returns a DNS response with the IP address and DNS TTL information  
- 10 - The system now has the IP address and initiates a TCP connection to the server
- 11 - TCP three-way handshake takes place, TLS Secure authentication process takes place and secure connection is setup.  
- 12 - HTTP(S)/HTML process begins to return information as required
