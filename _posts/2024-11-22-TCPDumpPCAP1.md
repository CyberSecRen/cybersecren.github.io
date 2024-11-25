---
layout: post
title:  "TCPDump PCAP Analysis Part One"
summary: "Using TCPDump to Analyse Packet Activity"
author: Renato Ferreira
date: '2024-11-22 14:35:23 +0530'
category: Packet_Analysis
thumbnail: /assets/img/posts/TCPDumpThumbnail.png
keywords: TCPDump, PCAP, analysis, packet analysis
permalink: /blog/TCPDump1/
usemathjax: true
---

<br><br>

# TCPDump Packet Capture Analysis Part One
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Questions:

1. How many UDP packets have been captured?
2. How many TCP packets have both the SYN and ACK flags set?
3. Which version of Chrome was used to connect to securityblue.team?
4. How many packets have a TTL value of 38?
<br><br>

## Solutions:
<br>

##### Question 1: How many UDP packets have been captured?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;After navigating to the directory where the PCAP file is saved, we can use the command `tcpdump -r SBT-PCAP4.pcap --count udp` to count the packets which match the UDP filter. The `-r` command is directing TCPDump to read the SBT-PCAP4.pcap file’s packets. The `--count` tells TCPDump to count the amount of packets which meet the filter criteria and finally, the `udp` command then tells TCPDump to count the UDP packets. TCPDump indicates there are 3290 UDP packets in the file.
<br>

![img-description](/assets/img/posts/TCPDumpIMG1.png)
<br><br>

##### Question 2: How many TCP packets have both the SYN and ACK flags set?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To count how many TCP packets contained both SYN and ACK, we must do some binary counting. The binary number for SYN and ACK flags would be 00010010, this translates to 18 for the decimal number. With this decimal number, we can now use the command `tcpdump -r SBT-PCAP4.pcap --count “tcp[13]==18”`. The `tcp[13]==18` expression tells TCPDump to look in the 13th byte of the TCP header which is associated with the flags and count how many of those packets match the decimal number we counted earlier. Alternatively, the `13` in the square brackets can be replaced with `tcpflags` to yield the same result. TCPDump indicates that it found 20 packets matching these criteria.
<br>

![img-description](/assets/img/posts/TCPDumpIMG2.png)
<br><br>

##### Question 3: Which version of Chrome was used to connect to securityblue.team?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To search for the browser version of Chrome that was used, we can use the command `tcpdump -r SBT-PCAP4.pcap -v | grep Chrome`. The `-v` allows for enough verbosity to see the version of Chrome used in the connection. `Grep` is used to search within a file which in this case was used to search for the keyword “Chrome”. The result shows that the Chrome browser that connected was running version 80.0.3987.87.
<br>

![img-description](/assets/img/posts/TCPDumpIMG3.png)
<br><br>

##### Question 4: How many packets have a TTL value of 38?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the packets which have a TTL value of 38, we can use the command `tcpdump -r SBT-PCAP4.pcap --count ip[8]==38`. This command tells tcpdump to refer to the 8th byte in the IP header which is associated with TTL (Time to Live) for the packet and count the ones in which this field is 38. This shows us there are 710 packets matching this criteria.
<br>

![img-description](/assets/img/posts/TCPDumpIMG4.png)
<br><br>
