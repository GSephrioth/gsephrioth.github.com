---
layout: post
title:  "Ch1:Overview of TCP/IP Protocol"
image: ''
date:   2017-03-22 11:15:00
comments: true
description: 'A menu of TCP/IP protocol'
series: TCP/IP
---

## network model

## layered network architecture
>higher layer use service provided by lower layer

## Basic divide of the layers
>mostly focus on transport/network/data-link layers

5. [Application]
4. [Transport] <- TCP/UDP
3. [Network] <- IP (packet)
2. [Datalink] <- physical address (frame)
1. [Physical]

## IP address (classful addressing)
* net-id & host-id
* classes and blocks
* packet (payload + header)
* network address
* special addresses
* private addresses
* unique/ multicast/ broadcast
* mask and routing
* subnetting (divide large blocks)
* supernetting (combine small blocks)

## IP address (classless addressing)
* variable length blocks
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
>mapping Logical address & physical address

* packet format
* encapsulation
* cache table
* queues
* input model
* output model
* cache control model

## Internet Protocol (IP)
>aim at end to end packet delivery

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
>aim at program to program delivery

* port number
* socket address (IP + port)
* connectionless serves (faster but not reliable)
* encapsulation and decapsulation
* UDP package

## Transmission Control Protocol  (TCP)
* process-to-process communication (P2P communication)
* connection-oriented service (reliable but slower)
* numbering system (in case of losing package)
* flow control (speed difference between processes)(slid window flow control)
* congestion control
* segment format
* encapsulation and decapsulation
* connection establishment and termination
* data transfer
* sliding window protocol
* TCP timers