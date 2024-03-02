# The Internet
- Internet connectivity :- 5G/4G connection, Wi-Fi network, Ethernet cable.
- IP address is assigned when it is connected to internet.
- IP address is composed of 4 sets of numbers, from 0 to 255.
- Router creates the local network and assigns every device that connects to it a different local IP address. So every device in your house has a different IP address.
- You can communicate between devices on your local network, but you cannot communicate with devices in other local networks, for example, the ones in your friend’s house, unless things are set up for this.
- Our devices can talk to the internet when they want, but the internet can’t talk to your devices unless you want it to and set up systems to do so.
- A server has an IP address, too.
- This time, the IP address is public because the server is created to be reached, unlike our home devices. The server has to be reachable all the time.
- A server also has a name, which we call a domain name.
- Other computers, called DNS servers, have the job of mapping a domain name to an IP address.
- Humans work best with names, computers work best with numbers. DNS makes it all very easy for both.
- The system that maps domain names to IP addresses is called DNS: Domain Name System.
- The language that computers use to talk to each other is called a protocol. The protocol that powers the internet we all know is called Internet Protocol Suite, also known as TCP/IP.
- On top of that layer, we have what we call transport protocols. They define how computers send packets of data to each other.
- TCP, also known as Transmission Control Protocol.
- This protocol makes sure packets are delivered from the client to the server, and from the server to the client.

## What is URL
- The URL is composed by the first part that determines the protocol.
- http:// or https:// signal we want to use HTTP or HTTPS (secure HTTP).
- Then we have the server address, which can be a domain name or an IP.
- Anything appended to the address part represents the document path.
- The web server is responsible for interpreting the request and, once analyzed, serving the correct response back to the client.

## What is a port
- When making network requests, you use an IP address, or a host name, and a port.
- It’s a technique introduced to allow multiple applications to respond on the same computer, on the same protocol.
- HTTP runs on port 80 by default.
- HTTPS runs on port 443 by default.
- FTP runs on port 21 by default.
- Every protocol has a different default port, but programs are not required to use that. They can use any unused port between 1 and 65535 (16 bits unsigned = 2^16).


## The DNS protocol
- The system that maps domain names to IP addresses is called DNS: Domain Name System.
- DNS is a network of servers. Your provider will have its own DNS, your router already preconfigured to use it.
- Those DNS servers will receive the requests from your computer, and in turn will ask their own reference DNS server.
- The system is organized like a tree. There is one DNS server at the top, called root DNS server.
- To simplify, it knows the IP address of the DNS servers that are managing each domain extension, like com, net, org and so on, including the country-specific domain extensions and the new ones like blog, dev or tech.
- Those DNS servers know the IP addresses mapping of all the domains under their extension.

## The TCP protocol
- TCP means Transfer Control Protocol, and it’s the basis of the Web and other applications like Email.
- TCP sits on top of the Internet Protocol (IP).
- Upon it, other application-level protocols like HTTP, FTP, IMAP (and many others) operate.
- TCP, contrary to IP and UDP, is connection oriented.
- Before transmission can happen over TCP, a connection must be established. Data is sent, in form of little packets, and when the communication ends the connection is closed.
- When data is transmitted over TCP, there’s a relatively complex workflow called handshake that must happen.
- If a packet gets lost, the protocol is able to handle it and the packet is re-sent.
- On the IP protocol, connections happen from computer to computer. In TCP, a connection happens from process to process, using the concept of ports.

## The UDP protocol
- UDP, User Datagram Protocol, is a transfer protocol, an alternative to TCP.
- Its main difference from TCP is that it’s connectionless.
- This implies that it’s faster, each packet sent is more lightweight, as it does not contain all the information needed in TCP, and it does have a lighter handshake process.
- The drawback is that UDP is not as reliable as TCP.
- In UDP, this is not built-in into the protocol, and must be handled at a higher level.
- UDP was defined in RFC 768 in 1980.
- The UDP protocol uses ports to allow communication between processes, like with TCP.
