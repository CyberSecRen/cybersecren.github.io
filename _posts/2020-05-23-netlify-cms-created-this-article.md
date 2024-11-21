---
layout: post
title:  "Wireshark PCAP Analysis Part Two"
summary: "Using Wireshark to Analyse Packet Activity"
author: Renato Ferreira
date: '2024-11-20 14:35:23 +0530'
category: Packet Analysis
thumbnail: /assets/img/posts/WiresharkThumbnail.png
keywords: Wireshark, PCAP, analysis
permalink: /blog/Wireshark2/
usemathjax: true
---

<br><br>

# Packet Capture Analysis Part Two
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Questions:

1. What is the WebAdmin password?
2. What is the version number of the attacker’s FTP server?
3. Which port was used to gain access to the victim Windows host?
4. What is the name of a confidential file on the Windows host?
5. What is the name of the log file that was created at 4:51 AM on the Windows host?
<br><br>

## Solutions:
<br>

##### Question 1: What is the WebAdmin password?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the password for WebAdmin, we can first start by searching in the packet details for the string “Webadmin”. To do this, we go to the Edit tab and use the find “Find Packet” function.
<br>

![img-description](/assets/img/posts/WiresharkIMG9.png)
<br>

Using the search bar, set the tabs to “Packet details”, “Narrow & Wide”, “String” and then type “Webadmin” into the search.
<br>

![img-description](/assets/img/posts/WiresharkIMG10.png)
<br>

This highlights an HTTP packet which contains a Dev-note stating that password.txt contains the webadmin password.
<br>

![img-description](/assets/img/posts/WiresharkIMG11.png)
<br>

![img-description](/assets/img/posts/WiresharkIMG12.png)
<br>

Now we can use password.txt as the search query in order to find a packet containing password.txt.
<br>

![img-description](/assets/img/posts/WiresharkIMG13.png)
<br>

This highlights another packet which contains a GET request for password.txt.
<br>

![img-description](/assets/img/posts/WiresharkIMG14.png)
<br>

We can follow the HTTP stream of this packet in order to find the password for WebAdmin. Here, it shows in cleartext that the WebAdmin password is sbt123.
<br>

![img-description](/assets/img/posts/WiresharkIMG15.png)
<br>

![img-description](/assets/img/posts/WiresharkIMG16.png)
<br><br>

##### Question 2: What is the version number of the attacker’s FTP server?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;In order to find the version of the attacker’s FTP server, we can right click on the source IP address from the password.txt request and apply the filter for Selected. This will apply a display filter for the source IP address which we can then filter further for only the FTP protocol requests.
<br>

![img-description](/assets/img/posts/WiresharkIMG17.png)
<br>

Here we can click on the first packet and look at the FTP section in the packet details and see that it states it is version 1.5.5 for the version of pyftplib (Python FTP library).
<br>

![img-description](/assets/img/posts/WiresharkIMG18.png)
<br><br>

##### Question 3: Which port was used to gain access to the victim Windows host?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;In order to find the port that was used to get access to the victim Windows host, set the display filter back to just the source IP address. We can find a string of `[ACK]` responses in order to see when the connection was made.
<br>

![img-description](/assets/img/posts/WiresharkIMG19.png)
<br>

Here, we can see that the port used to gain access was Port 8081.
<br>

![img-description](/assets/img/posts/WiresharkIMG20.png)
<br>

![img-description](/assets/img/posts/WiresharkIMG21.png)
<br><br>

##### Question 4: What is the name of a confidential file on the Windows host?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the name of a confidential file on the host computer, I kept the source IP filter and followed the TCP Stream on one of the packets which brought up a window which showed the contents of the desktop.
<br>

![img-description](/assets/img/posts/WiresharkIMG22.png)
<br>

In this new window, it shows a file called “Employee_Information_CONFIDENTIAL.txt”.
<br>

![img-description](/assets/img/posts/WiresharkIMG23.png)
<br><br>

##### Question 5: What is the name of the log file that was created at 4:51 AM on the Windows host?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the log file, I stayed on the same window that was brought up by following the TCP Stream and in the list of files there was one by the name of LogFile.log which was created at 4:51am.
<br>

![img-description](/assets/img/posts/WiresharkIMG24.png)
<br>
