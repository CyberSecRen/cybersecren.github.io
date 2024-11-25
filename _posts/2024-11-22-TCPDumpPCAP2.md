---
layout: post
title:  "TCPDump PCAP Analysis Part Two"
summary: "Using TCPDump to Analyse Packet Activity"
author: Renato Ferreira
date: '2024-11-22 14:35:23 +0530'
category: Packet_Analysis
thumbnail: /assets/img/posts/TCPDumpThumbnail.png
keywords: TCPDump, PCAP, analysis, packet analysis
permalink: /blog/TCPDump2/
usemathjax: true
---

<br><br>

# TCPDump Packet Capture Analysis Part One
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Questions:

1. What is the name of the PNG file on the webserver at 192.168.56.111?
2. Which version of OpenSSH is running on the server?
3. On which port is the .zip file being served?
4. When was a packet with a TCP checksum value of 53203 captured? (Format: xx:xx:xx.xxxxxx)
<br><br>

## Solutions
<br>

##### Question 1: What is the name of the PNG file on the webserver at 192.168.56.111?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the name of the PNG file on the webserver we can use the command `tcpdump -A -r SBT-PCAP5.pcap | grep .png`. The `-A` parameter is used to display results in ASCII and since we are looking at a webserver, this parameter will help produce the results we need. We then use `grep .png` in order to look for any file that has a .png file. We can see the result that was given is a file named “proprietary.png”.
<br>

![img-description](/assets/img/posts/TCPDumpIMG5.png)
<br><br>

##### Question 2: Which version of OpenSSH is running on the server?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the version of OpenSSH we can use `tcpdump -r SBT-PCAP5.pcap | grep OpenSSH`. Looking for OpenSSH within the file using `grep` shows us that the server is running OpenSSH 7.9p1.
<br>

![img-description](/assets/img/posts/TCPDumpIMG6.png)
<br><br>

##### Question 3: On which port is the .zip file being served?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the port for the .zip file, we can use `tcpdump -A -r SBT-PCAP5.pcap | grep “.zip” -B 3`. This allows us to see the .zip file and the `-B 3` allows us to see 3 lines before it which shows additional header information and here we can see the port on which it is served. The port is 3016.
<br>

![img-description](/assets/img/posts/TCPDumpIMG7.png)
<br><br>

##### Question 4: When was a packet with a TCP checksum value of 53203 captured? (Format: xx:xx:xx.xxxxxx)
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To look for this checksum value, we can use `tcpdump -r SBT-PCAP5.pcap “tcp[16:2]=53203”`. The `tcp[16:2]=53203` is used to look at the checksum part of the header which is 2 bytes and starts at byte 16, within these 2 bytes, it searches for a checksum value of 53203. We can use the results to see what time the packet was captured. Based on this result, we can see the packet was captured at 06:04:46.207925.
<br>

![img-description](/assets/img/posts/TCPDumpIMG8.png)
<br><br>