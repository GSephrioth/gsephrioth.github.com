---
layout: post
title:  "TCP/IP protocol suite"
image: ''
date:   2017-01-19 13:50:00
description: ''
serie: learn
---

Lecture 2 & 3

<h1 style="color:grey">Overview</h1>

## network model

## layered network arctitecture
>highter layer use service provided by lower layer

## Basic divies of the layers
>mostly focus on transport/network/dataline layers
	5. [application]
	4. [transport] <- TCP/UDP
	3. [network] <- IP (packet)
	2. [dataline] <- physical address (frame)
	1. [physical]

## IP address (classful addressing)
* netid & hostid
* classes and blooks
* packet (payload + header)
* network address
* special addresses
* private addresses
* unique/ mulitycast/ boardcast
* mask and routing
* subnetting (divide large blocks)
* supernetting (combine small blocks)

## IP address (classless addressing)
* varable length blocks
* subnetting
* address location with Egs.

## delivery and forwarding and routing of packets
* direct/ indirect delivery
* routing table
* forwarding techniques
* forwarding with classful addressing
* forwarding with classless addressing
* static/ dynamic routing

## Address Resolution Protocol (ARP)
>maping Logical address & physical address

* packet format
* encapsulation
* cache table
* queues
* input model
* output model
* cache control model

## Internet Protocol (IP)
>aim at end to end packet deliverly

* datagram
* fragmentation (adjust size of packet to suit different frames)
* options
* header adding model
* processing model
* queues
* routing table
* forwarding model
* reassembly model
* reassembly table

## User Datagram Protocol (UDP)
>aim at program to program deliverly

* port number
* socket address (IP + port)
* connectionless serves (faster but not reliable)
* encapsulation and decapsulation
* UDP package

## Transmission Control Protocol  (TCP)
* process-to-process communication (P2P communication)
* connection-oriented service (reliable but slower)
* numbering system (incase of loseing package)
* flow control (speed difference between processes)(slid window flow control)
* congestion control
* segment format
* encapsulation and decapsulation
* connection establishment and termination
* data transfer
* sliding window protocol
* TCP timers

Lecture 4

<h1 color="grey">Layer articture</h1>

The Internet model sometimes caused the TCP/IP protocol suit is composed of five levels:
	5. [application]
	4. [transport]
	3. [network]
	2. [dataline]
	1. [physical]

In developing these model the desingers distilled the process of transmitted data to its host fundemental elements. Identify the networking fection and collect these fections into dis.. form Layers. Each layer defines a family of fections distinctive from these of each layer.

Each layer build upon the service of the layer below it. eg. layer 3 is based on the service of layer 2, and provides service to layer 4. Layer X on one machine communicates with Layer X on other machine.

It costs quite a lot to change a protocol, especially when it does not suits the interface of upper layer and below layer. Because change of interface means change the protocol, which result into a change of the whole networking system. That is a revolution.

As long as a layer....

At each layer a Header can be added to the data unit. at layer 2 a T.. is added as ...

## Physical Layer

the physical layer is responsible for transmitting individal bits from one node to the next.

the major dvties of the physical layer: Physical characterisitics of .... and .... The physical layer defines charcateristics of the interface ...............

representation of logical bits: voltage, light, etc. Most times we use +5V trans to -5V to represent logical 1; -5V trans to +5V to represent logical 0. Because that way we will not get a constant signal +5V, which is hard to decide the beginning and the end of each bit.

Data rate
The transmission layer ...... of a bit.

Synchronization of bits (difference of CPU clock might cause a problem)






