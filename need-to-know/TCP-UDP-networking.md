Have you ever heard about cloud like cloud services or something like that? The cloud is really just a whole bunch of actual computers somewhere else in the world. A cloud computer isn't really a cloud computer. It's really someone else'computer.

AWS, Azure are cloud services, right? They have cloud computers available? But this actually has real computers in their data centers in Ohio, Viginia, Singapore... So the cloud is actual computers that just don't belong to you.

So the intenet is looking like where you've  got computer talking to computer and these are talking to another one... And what's actual passed around, we call packet ~ little stream of data.

                            Packet          Examples:
                        _____________________________________
                        | Application | ~ HTTP, SSH, FTP... |
                        | Transport   | ~ TCP/UDP           |
                        | Network     | ~ IP                |    
                        |  Link       | ~ wifi, intranet    |
                        |  Physical   | ~ Cable...          |
                        |___________________________________|


                        Client machine <==== Data ~ Packet ===> Server machine

Packet have 5 basic layers structure(OSI model ~ 7 layers in details) above.

You have a computer with some kind of internet connection. The trasport layer creates about 65,535 ports. Well-known ports (0 to 1023) are commonly used by HTTP, SMTP, DNS and so on. Registered ports (1024 to 49151) are assigned to user process application that you install on your computer need to connect to internet. Dynamic or private ports (49152 to 65535) is for another.  

The request will be handle off to the transport layer and that will get wrapped up in what's called `segment`. Inside a segment, there'll be metadata and It will have destination port, source port. This segment will hand that off the network layer for the further processing.

There are two different types of transport layer protocols:
<h3>1. UDP</h3>

 - incredibly lightweight(only 8 bytes for a header)

 - connection loss: When you want to send data, you don't create connection, just send data to target computer. And even if this computer doesn't want to hear from you, It's ok. You don't have to wait for the connection to be established. 

 - consistency: UDP can send data no matter what, that might be seen as a very good thing, but It can be a trouble. What happens if there's packet loss?  UDP doesn't not care. It will still sending packets. What if the network is very congested ? It doesn't care. What happens if the packets are out of order? It's not a UDP problem.
 
  You can notice that by playing video games like LOL, ... sometimes, the character being moving back to previous or something like we normally call laggy.

Those seems bad but UDP has a really big win, FAST. But It's also incredibly unreliable

<h3>2. TCP:</h3>

 - Connection based: You actually go through what's call a three way handsake, because before you 're going to actually transmit any data, you have initiate a connection. Way 1: you request. Way 2: targetmachine appove. Way 3. Connection is establised.

 - Reliable: You know what's you sent. Ok. It also as delivery acknowledgements, which just mean when data is comes through, the server on the right hand side over here will let the client know that they got the data. 

 - Restranmisstion of data. UDP may not even know that whether data was received or not. With TCP, if the data isn't received, the server can let the client know they didn't get something and the client can send it again.

 - consitency: TCP can gurantee the client gets in order packets. 

 - congestion control

 In our case, web development, we absolutely need TCP because we need all of the reliability that TCP has offer. If we send a web page to a user, we can't have the packet showing up the different order or the HTML will show up in completely the wrong order or css will show  wrong order 

 ![Data flow](https://microchipdeveloper.com/local--files/ethernet:overview/data-flow-tx.png)