---
layout: post
title:  "Ch2:Layers of TCP/IP Protocol"
image: ''
date:   2017-03-22 11:15:00
comments: true
description: 'Introduction of all layers in TCP/IP protocol'
series: TCP/IP
---

>The Internet model sometimes caused the TCP/IP protocol suit is composed of five levels:

5. [Application]
4. [Transport]
3. [Network]
2. [Datalink]
1. [Physical]

In developing these model the designers distilled the process of transmitted data to its host fundamental elements. Identify the networking faction and collect these factions into dis.. form Layers. Each layer defines a family of factions distinctive from these of each layer.

Each layer build upon the service of the layer below it. e.g. layer 3 is based on the service of layer 2, and provides service to layer 4. Layer X on one machine communicates with Layer X on other machine.

It costs quite a lot to change a protocol, especially when it does not suits the interface of upper layer and below layer. Because change of interface means change the protocol, which result into a change of the whole networking system. That is a revolution.

As long as a layer provides the expected service to the layer above it. The specific implementation of its function can be modified or replace without requiring changes to the surrounding layer.

At each layer a Header can be added to the data unit. At layer 2 a Trailer is added as well.

<h1 style="color:grey">Physical Layer</h1>

>the physical layer is responsible for transmitting individual bits from one node to the next.

the major duties of the physical layer: 
1. Physical characteristics of interfaces and media
The physical layer defines characteristics of the interface between the divides and the transmission meaning. It also defines the type of transmission media.

2. representation of logical bits
Voltage, light, etc. Most times we use +5V trans to -5V to represent logical 1; -5V trans to +5V to represent logical 0. Because that way we will not get a constant signal +5V, which is hard to decide the beginning and the end of each bit.

3. Data rate
The transmission rate is also defined by the physical layer. The physical layer defines the duration of a bit.

4. Synchronization of bits 
Difference of CPU clock might cause a problem.

<h1 style="color:grey">Data Link Layer</h1>

>Data Link Layer is to organize bits into frames, to provide hop-to-hop delivery.

The major duty of the data link layer:

1. Framing: 
The data link layer divides the stream of bits into manageable data units called "Frames". It contains Trailer, Data from network layer, Source address, Destination address.

2. Physical Addressing: 
The data link layer adds a header of the frame to define the sender and receiver of the frame. Most of the time, it also called as Media Access Control(MAC) address.

3. Flow Control:
If the data absorb by the receiver is less than the rate produced by the sender, the data link layer imposes a flow control mechanism to prevent overwhelming the receiver.

4. Error Control:
The data link layer adds mechanisms to defect and retransmit damaged or lost frames. Error control is achieved through a trailer added to the end of the frame.

5. Access Control:
When two  or more devices are connected to the same link. Data link layer predicts are necessary to determine which device has control over the link at any given time.

<h1 style="color:grey">Network Layer</h1>

>The network layer is responsible for the delivery of packets from the original source to the final destination, possibly across multiple networks.

Packet do not change during the end to end transfer, which means the packet may pass through several router and change the frame covering it for several times.

The major duty of the network layer:

1. Logical Addressing:
The network layer adds a header to the data unit coming from the upper layer that includes the logical address of the sender and receiver.

2. Routing:
When independent networks or links are connected to create an internetwork. The connected devices route the packets to their final destination. The network layer provides this mechanism.

3. Internetworking:
The network layer at the source computer needs to consult a routing table to find the logical address of the next hop.

4. Packetizing
Encapsulating the data coming from the upper layer in a datagram. This is done by adding a header to the data that contains the logical source and destination address of the packet, information about fragmentation, the protocol ID of the protocol that has requested the service, the data length, and possibly some options. 

5. Fragmentation:
The datagram needs to be fragmented to smaller units before being passed to the data link layer. Fragmentation needs to preserve the information at the header of the datagram.

6. Address Resolution:
Use a table to map the logical address of the next-hop into MAC address of the next-hop.

<h1 style="color:grey">Transport Layer</h1>

>The transport layer is responsible for delivery the message from process to process.

The major duty of the transport layer:

1. Port addressing:
The transport layer header must includes a port address. The network layer get each packet to the traffic computer. The transport layer get the entire message to the certain process on that computer.

2. Segmentation and the reassembly:
A message is divided into transmittable segments, each segment connecting A sequence number. These numbers enable the transport layer to reassemble the messages correctly upon arrival to the destination.

3. Connection Control:
The transport layer can be either connectionless or connection oriented. A connectionless transport layer treats each segments as a independent unit and deliver it to transport layer at the destination machine. A connected oriented transport layer crates a connection with the transport layer at the destination machine before transferring the segments. After all the data are transfered the connection is terminated.

4. Flow Control:
Flow control at this layer is performed end-to-end rather than across a single link.

5. Error control:
Error control at this layer is performed end-to-end rather than across a single link. To sending transport layer to make sure that the entire message arrives at the receive transport layer without errors. 

<h1 style="color:grey">Application Layer</h1>

>The application layer is responsible for providing services to the user.

Main services: FIle Transfer/ WWW

<h1 style="color:grey">Open System Interconnection(OSI) Model</h1>

>It is developed by International organization for standardization(ISO). The OSI model is a theoretical model describe to show how a protocol stack should be implemented.
	
7. [Application]
6. [Presentation]
5. [Session]
4. [Transport]
3. [Network]
2. [Datalink]
1. [Physical]

The <label style="color:red">Session Lay</label> is the network dialog controller. It was designed to establish maintain an Synchronize the interaction between communicating system.

The <label style="color:red">Presentation Layer</label> were designed to handle syntax and semantics of the information changes between the systems. It was designed for data translation, Encryption, decryption and compression.