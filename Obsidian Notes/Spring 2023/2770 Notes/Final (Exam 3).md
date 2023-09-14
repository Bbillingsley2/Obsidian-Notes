
- Networking and ISO Model (Slides 1-17)
	- Know that layering is an approach for building system's software and, in particular, protocol stacks. Know that the OSI model is a layered model. Know that the OSI model was established by the ISO. Be able to describe the OSI model's purpose.
	- Be able to list and describe the purposes of each of the OSI model's layers. Understand how each layer encapsulates data from a higher layer in its own representation with added headers and, possibly, trailers.
	- Data Link Layer: know what framing is and why it is needed. Be able to describe the purpose of the data link layer.
	- Network Layer. Know what it meanst by _hop-by-hop delivery_.   Be able to describe the purposes of the network layer, including both delivery and addressing.  Be able to describe the picture on slide 11.
	-   Transport Layer: be able to describe the purposes of the network layer, including both delivery and addressing.  Know what is meant by _reliable delivery, process-to-process deliver,_ and _in-order delivery_.
	-   Understand how the TCP/IP protocol suite fits into the OSI model (See slide 17)

Chapter 11 - Network Programming

-   Be able to describe the client-server model.   Know how a request-response protocol behaves. 
-   Know what a NIC is. **Network Interface Card that is connected to a wire that is able to take the data that you give and make a signal**
-   Know the architecture of Ethernet and how it behaves as a bus network.  Know what a hub it.  Know the difference between a hub and a bridge. **The bridge is smarter than the hub and learns whose address is what, it looks and learns over time.**
-   Know what an internet is and the difference between a bridge and and router.  Be able to describe the purpose of a router. **The internet is a bunch of connected networks. We need routers because they are smarter than bridges and thy can handle different kinds of networks such as wireless and ethernet. Routers know how to talk between network who are not compatible with each other. They understand the network level address.**
-   Be able to define TCP, IP, and sockets in terms of their layering, capabilities, and purpose. **TCP is your transport layer protocol and is in order, reliable, and the ability to address process. IP**
-   Know what an IP address is (slide 25-27). **It is a 32 bit number (IPv4) that can expressed in dotted decimal notation. **
-   Be able to use the functions htonl( ),  htons( ), ntohl( ), and ntohs( ) to convert between host and network byte order, and vice versa.  Know why these functions are needed. **these functions are needed because we have machines that have things in different byte orders**
-   Be able to read dotted decimal notation.  Be able to convert between dotted decimal notation and 32-bit IP addresses. **You take the first number before the dot and turn it into hex, second number into the hex, etc. and then covert hex to decimal**
-   Know how Domain Names work (their hierarchical structure) and know about the Domain Name System (DNS).   Know how to use nslookup and hostname.  Also know that a host can have more than one domain name. 
- Be able to define the terms point-to-point, full duplex, reliable, in-order delivery as they pertain to communication over the Internet.
-   Know what a socket is.  Know what a port is.  Know what a ephemeral port is.  Know what a well-known port is. **A socket it is family function used to talk over a network. A port is the abstraction that TCP uses to identify processes.**
-   Know how the client-server model operates (the roles, and request-response paradigm).

Chapter 11, Sections 4-6 - Web Servers and the HTTP Protocol

-   Know what the following client socket functions do: connect(), send(), receive(), close()
**the connect function attempts to establish an internet connection with the server at socket address addr. Send is done in the the client and the server. Recieve can be done by both. Close can be done by both.**
-   Know what the following server socket functions do: bind(), listen(), accept(), send(), receive(), close()
-   Know which socket functions are used for clients and which are used for servers.
-   Know how to use fdopen() to turn a socket descriptor into a FILE pointer.  Know what the advantages of using a FILE pointer are. **sockets are low level file descriptors that you can use low level api's. if you turn it into a file pointer you can do more like send lines instead of just bytes.**
-   You should be able to complete a simple socket client or server program.  You should be able to identify the parts of a simple client or server program.
**given a server program and need to put the name of the api call name**
-   Know what HTTP stands for, what its purposes are, and how it fits into the protocol stack.
**Hyper Text Transfer Protocol. Purpose is to be able to handle documents. It is an application level protocol**
-    Know that HTTP is a client-server, request-reply protocol.
-   Know what HTML is.  Know what a markup languages is and how they differ from an imperative languages such as C++ or Java.
**markup langauges doesnt do anything, it just scribes. imperative languages does steps.**
-   Know what MIME types are and why they are needed.
**Multipurpose internet mail extensions. They are needed because when we send raw bytes, when they reach the other side, they might not know what to do with them**
-   Know what static and dynamic content are. **when dealing with http, static is when you fetch a disk file and return its contents to the client. dynamic is when you run an executable file and return its output to the client**
-   Know what a URL is and how one is formatted.  Know is parts and each of their purposes. **universal resource locator. the first part (http://) describes the protocol, the second part (www.google.com) is the domain name, the third part (:80) is the port number, the fourth part (/index.html) is the resource**
- Know the format and purpose of the query that can come at the end of a URL.  Be able to construct a URL given a description.
	-   Know what is meant by the _server's root directory_, and how it relates to a URL.
-   Know the structure and syntax of an HTTP GET request and be able to identify its parts.  Know the purpose of the Content-Type and Content-Length headers.  Know the syntax and purpose of each part of the GET request line
-   Know the struct and syntax of an HTTP reponse. Know the syntax and purpose of each part of an HTTP response line.  Know the following response codes: 200, 401 (unauthorized), 403, and 404.
-   Know how servers serve dynamic content.  Understand the basics of how the query string is passed to the program that the server runs (Via global arrays for language modules, and via environment variables for CGI).  Know how the programs results are collected by the server.