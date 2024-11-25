---
layout: post
title:  "Wireshark PCAP Analysis Simulation"
summary: "Using Wireshark to Analyse Packet Activity in Scenario Simulation"
author: Renato Ferreira
date: '2024-11-20 14:35:23 +0530'
category: Packet_Analysis
thumbnail: /assets/img/posts/WiresharkThumbnail.png
keywords: Wireshark, PCAP, analysis, packet analysis
permalink: /blog/Wireshark3/
usemathjax: true
---

<br><br>

# Wireshark Packet Capture Analysis Part One
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Scenario:
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Alevis is a fictional cybersecurity company with thousands of employees. An attacker has gained unauthorized entry into its premises and has connected their laptop to an unused port on a switch. The attacker now has access to the company’s internal networks. Within the internal network, there is a central server where critical proprietary data is stored. In this capture, the attacker is attempting to collect SSH credentials that they can use to log into the central server. Using a sample packet capture file, answer the following questions.
<br>

## Questions

1. What is the MAC address of the attacker?
2. What is the type of attack which is taking place that allows the attacker to listen in on conversations between the central server and another host?
3. What is the file which was downloaded from the central server?
4. What department does Borden Danilevich work in?
5. What is the SSH password of the Domain Administrator?
<br><br>

## Solutions
<br>

###### I will be using Wireshark for the purposes of this PCAP analysis.
<br>

##### Question 1: What is the MAC address of the attacker?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Since we know the attacker is attempting to collect SSH credentials, we can start by filtering the captured packets so that we only have to investigate SSH packets and get rid of everything else. Once we have filtered only the SSH packets, I used the statistics tab to check for how many systems were using SSH and there are only 2 shown in the Conversations tab. This means one is the attacker and the other is the server. If we look into the packet details and open up the Ethernet II section, we can look at the source MAC address of the first packet that the client system sent. Here, we can see that the MAC address of the attacker is 08:00:27:3d:27:5d.
<br>

![img-description](/assets/img/posts/WiresharkIMG25.png)
<br><br>

##### Question 2: What is the type of attack which is taking place that allows the attacker to listen in on conversations between the central server and another host?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;This form of attack is called a man in the middle attack. The attacker uses their own packet capture used in between two systems that are communicating in order to extract data from those packets.
<br><br>

##### Question 3: What is the file which was downloaded from the central server?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find out which file was downloaded, we can try filtering for common protocols used file transfers such as FTP. If we begin by filtering all the traffic to only find FTP, we narrow the search down to only 12 packets. We can easily look through the info section of these packets and see that there is a RETR request for a file named “Alevis_Employee_Information_Chart.csv” and we can see in the following packets that the transfer was complete and so this was the file downloaded from the central server. Alternatively, before trying to filter for FTP, we could use the Protocol Hierarchy in the Statistics tab and look under TCP. Here we would see that there were SSH and FTP packets which would have directed us to look at FTP for these transfers.
<br>

![img-description](/assets/img/posts/WiresharkIMG26.png)
<br><br>

##### Question 4: What department does Borden Danilevich work in?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the answer to this, we will use the employee information file that was downloaded. We can do this by following the TCP Stream of the FTP packet we found in the previous question which will bring us to the Stream 0 page. If we select Stream 1 in the bottom right corner, we can see many lines of employee information.
<br>

![img-description](/assets/img/posts/WiresharkIMG27.png)
<br>

Typing Borden into the search bar at the bottom brings up Borden Danilevich’s information including the fact that he works in the Sales department.

![img-description](/assets/img/posts/WiresharkIMG28.png)
<br><br>

##### Question 5: What is the SSH password of the Domain Administrator?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Using the same TCP Stream from the last question, we can simply search for the name “Admin” and find the details for the Domain Admin account. The password for this account is "gMR<4eXf]e6W".
<br>

![img-description](/assets/img/posts/WiresharkIMG29.png)
<br><br>