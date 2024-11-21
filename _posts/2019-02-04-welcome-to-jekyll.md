---
layout: post
title:  "Wireshark PCAP Analysis Part One"
summary: "Using Wireshark to Analyse Packet Activity"
author: Renato Ferreira
date: '2024-11-20 14:35:23 +0530'
category: Packet Analysis
thumbnail: /assets/img/posts/WiresharkThumbnail.png
keywords: Wireshark, PCAP, analysis
permalink: /blog/Wireshark1/
usemathjax: true
---

<br><br>

# Packet Capture Analysis Part One
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Questions:

1. Which protocol was used over port 3942?
2. What is the IP address of the host that was pinged twice?
3. How many DNS query response packets were captured?
4. What is the IP address of the host which sent the most number of bytes?
<br><br>

## Solutions:
<br>

##### Question 1: Which protocol was used over port 3942?

Using the display filter `udp.port == 3942` displays that the protocol used on this port is SSDP
<br><br>

![img-description](/assets/img/posts/WiresharkIMG1.png)
<br><br>
&nbsp;&nbsp;&nbsp;&nbsp;Alternatively, the Statistics tab could also be used to search for this answer. Going into the Endpoints window inside of the Statistics tab and then using the UDP tab to find the Port number and IP address associated with it and apply this as a display filter will display only the results matching this criteria.
<br><br>

![img-description](/assets/img/posts/WiresharkIMG2.png)
<br><br>

![img-description](/assets/img/posts/WiresharkIMG3.png)
<br>
<br>

##### Question 2: What is the IP address of the host that was pinged twice?

&nbsp;&nbsp;&nbsp;&nbsp;In order to find ping packets, the associated filter is `icmp` which can be used as a display filter to find which IP address was pinged. Here we can see that ping requests came from 192.168.1.7 and it was pinging 8.8.4.4 and so that is the IP of the host that was pinged which then returned a reply.
<br><br>

![img-description](/assets/img/posts/WiresharkIMG4.png)
<br>
<br>

##### Question 3: How many DNS query response packets were captured?

&nbsp;&nbsp;&nbsp;&nbsp;In order to find how many DNS query response packets were received, the first step will be to use the display filter in order to filter for just DNS packets in general by typing `dns` or alternatively, typing `udp.port == 53` (port 53 is associated with DNS) into the field. Next, typing `dns.flags.response == True` will bring up only the DNS packets which contain a response flag which filters out all the query packets. Alternatively, clicking on a DNS response packet and finding the response flag and using “apply as filter” > “Selected” as a filter will also achieve the same result. There are 90 packets displayed with these filters and so that means that there were 90 DNS response packets captured.
<br><br>

![img-description](/assets/img/posts/WiresharkIMG5.png)
<br><br>

![img-description](/assets/img/posts/WiresharkIMG6.png)
<br><br>

![img-description](/assets/img/posts/WiresharkIMG6.png)
<br><br>

##### Question 4: What is the IP address of the host which sent the most number of bytes?

&nbsp;&nbsp;&nbsp;&nbsp;In order to find the IP address of the host which sent the most number of bytes we must use the Statistics tab and go to Endpoints. In the IPv4 tab within the Endpoints window, it is possible to sort the number of “Tx Bytes” (Transmitted bytes) by clicking on the tab to sort it into descending order. This shows that 115.178.9.18 sent the most bytes at 2MB.
<br><br>

![img-description](/assets/img/posts/WiresharkIMG8.png)