---
layout: post
title:  "TCP/IP protocol suite"
image: ''
date:   2017-04-04 10:00:00
comments: true
description: 'Lectures in IIT about TCP/IP protocol suite'
series: Notes
---
<h1 style="color:grey">User Datagram Protocol</h1>
UDP is connectionless unreliable transport protocol. It does not add anything to the service of IP except for providing <label style="color: red;">Process-to Process</label> communication instead of Host-to-Host communication.
A process is a running application program. Identified by the "port" number.

UDP is a simple protocol, does not provide flow control mechanism and there is no acknowledgment for received UDP datagram. 

For communication we must define 
- local host 
- local process
- remote host
- remote process

The client-server paradigm
A process on the local host called a <label style="color: red;">Client</label> needs services from a process usually on the remote-host called <label style="color: red;">Server</label>

The local host and the remote host are defined using IP addresses.
To define the processes we need Identifiers called <label style="color: red;">Port numbers</label>

The client program defines itself with a port number called <label style="color: red;">The ephemeral port number</label>.(临时端口)
The server use universal port number an they are called <label style="color: red;">well-known port number</label>.(常用端口)

The destination IP address defines the host among the different hosts in the world. After the host has been selected the port number defines one of the processes on this particular host.

<p style="color:red">Lecture 25</p>

<label style="color: red;">Well-known ports</label> The ports ranging from 0-1023 are assigned and controlled by ICANN internet corporation for assigned names and numbers.

<label style="color: red;">Registered ports</label> The ports ranging from 1024-49151 are not assigned or controlled by ICANN. They can only be registered  with ICANN to prevent dupucation.

<label style="color: red;">Dynamic or private</label> The ports ranging from 49152-65535 are neither controlled nor registered. They can be used as temporary or private port numbers.

<img src="Figure11.4">
Socked address = IP address + Port number
The combination of an IP address and a port number is called a <label style="color: red;">socket address</label> The client address defines the client process uniquely just as the server socket address defines the server process uniquely.

<img src="Figure11.7">
UDP datagram format

The UDP datagram have a fixed-size header of 8 bytes.
* <label style="color: red;">Source port number</label> If the source host is the client, the port number is an *ephemeral port number* If the source host is the server, the port number is a well-known port number.
* <label style="color: red;">Destination port number</label> Same story as the source port number.
* <label style="color: red;">Length</label> This is a 16-bit field that defines the total length of the UDP datagram. 
* <label style="color: red;">Checksum</label> Error detection.

UDP provides a connectionless service.
The user datagram are not numbered.
There is no connection establishment and no connection termination.

The queues opened by the client are identified by ephemeral port numbers. The queues function as long as the process is running. When the process terminates the queues are destroyed.

At the server side the mechanism of creating queues is different. A server asks for incoming and outgoing queues using its well-known port. When it starts running the queues remain open as long as the server is running, even the process terminated.

<img src="Figure11.13">
The UDP package involves the following components:
- Control-block table
- Control-block module
- Queues
- Input module
- Output module


<label style="color: red;"> Control-block table </label> keeps track of the open ports each entry in this table has four fields.
* State: "Free" or "In-use"
* Process ID
* Port number
* Queue number

The Control-block module is responsible for the management of the control-block table. When a process starts, it asks for a port number from the operating system. The process passes the process id, and the port number to the control-block nodule to create an entry in the table for the process.

1. Search the control-block table for a "Free" entry
2. If not found, delete an entry using a predefined strategy.create a new entry with the state "In-use", create the process id and the port number.
	 *Homework: what strategy will we use*

The input module receives a user datagram from the IP layer. It searches the control-block table to find an entry having the same port number as this user datagram. If the entry is found, the module uses information in the entry to enqueue the data.

1. Look for the corresponding entry in the control-block table.
2. If found, check the queue field to see if a queue is allocated.
3. If it is not a allocate a queue. Enqueue the data in the corresponding queue.
4. If not found, discard the datagram, use ICMP to send an error message.

<h1 style="color:grey">TCP</h1>
TCP is a process-to-process protocol. TCP uses port numbers. TCP is connection-oriented, reliable protocol. It adds connection oriented and reliability features to the service of IP.

TCP allows the sending process to deliver data as stream of bytes and allows the receiving process to obtain data as a stream of bytes. 

TCP creates an environment in which the two processes seem to be connected by an Imaginary "Tube" that carries their data across the internet.
<img src="Figure12.4">

At the transport layer TCP groups a number if bytes together into a data unit called <label style="color: red;">Segment</label>. TCP adds a header to each segment and delivers the segment to the IP layer for transmission. The segments are encapsulated in an datagram and transmitted.

TCP offers full-duplex service, where data can flow in both directions at the same time.

TCP is a connection-oriented protocol. When a process at site *A* wants to send and receive data from another process at site B. 
1. The two TCPs establish a connection between them.
2. Data are exchanged in both directions.
3. The connection is terminated.

Numbering system
There are two fields called the <label style="color: red;">sequence number</label> and the <label style="color: red;">acknowledgment number</label>. These two fields refer to the byte number not the segment number.

The numbering starts with a randomly generated number.
After the bytes have been numbered TCP assigns the sequence number to each segment that is being sent. The sequence number of each segment is the number of the first byte carried in the segment.

The value of the acknowledgment field is a segment defines the number of the next byte a party expects to receive.
The acknowledgment number is cumulative.
The term cumulative means that if a party uses 5643 as an acknowledgment number, it has received all bytes from the beginning up to 5642.

TCP provides <label style="color: red;">Flow control</label>.
The receiver of the data controls how much data are to be sent by the sender. This is done to prevent the receiver from being overwhelmed with data.

TCP takes into account <label style="color: red;">congestion control</label> in the network. The amount of data sent by a sender is also determined by the level of congestion in the network.

<img src="Figure12.5">
TCP segment format

The segment consists of a 20~60 byte header followed by data from the application program. 
- Source port address
- Destination port address
- Sequence number
	This 32-bit field defines the number assigned to the first byte of data contained in this segment.
- Acknowledgment number
	This 32-bit field defines the byte number that the receiver of the segment is expected to receive from another party.
	Acknowledgment and data can be piggybacked together.
- Header Length(HLEN)
	This 4-bit field indicated the number of 4-byte words in the TCP header. The length of the header can be between 20 and 60. So this can be between 5 and 15.


<p style="color:red">Lecture 26</p>

- Control
	This field defines 6 different control bits or flags. One or none of these bits can be set at a time. 
	URG自己补全
	ACK
	PSH
	RST
	SYN
	FIN
- Window size 有点复杂，自己仔细查下
	This field is defines the size of the windows size in bytes. The other party must maintain. This values is determined by the receiver. The sender must obey the dictation of the receiver in this case.
	RWND: Receivers windows size
	CWND: Congestion window size

- Checksum
- Urgent pointer

Connection establishment using <label style="color: red;">Three-way handshaking</label>
<img src="Figure12.9">
1. The client sends the first segment, a "SYN" segment in which only the "SYN" flag is set. This segment is for synchronization of sequence numbers. The client choose a random number as the first sequence number.
The "SYN" segment is a control segment. And does not carry any data. However, it consumes one sequence number.

2. 

Data transfer
<img src="Figure12.10">

Connection termination using <label style="color: red;">Three-way handshaking</label>
<img src="Figure12.11">

Sliding window
Window size = min(rwnd, cwnd)
move the closing on the left according to receiving ACK
move the opening on the right according to closing + window size 
Shrinking window when rwnd or cwnd is reduced. This situation is not allowed in most implementation.
