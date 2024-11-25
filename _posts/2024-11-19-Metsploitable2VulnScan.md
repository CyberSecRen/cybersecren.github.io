---
layout: post
title:  "Vuln Scanning Practice in Metasploitable 2"
summary: "Using Metasploitable 2 to Practice Vuln Scanning and Enumaration"
author: Renato Ferreira
date: '2024-11-19 14:35:23 +0530'
category: Pentesting
thumbnail: /assets/img/posts/MetasploitThumbnail.png
keywords: vulnerabilities, metasploitable, pentesting, bash
permalink: /blog/metasploitable/
usemathjax: true
---

<br><br>

# Performing Basic Vuln Scan on Metasploitable 2 VM
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

##### After creating a Metasploitable 2 VM, I am using a Kali Linux VM in order to do a basic port scan for vulnerabilities in the MS2 VM and answering the following questions:
<br>

## Questions:

1. Which company created Metasploit?
2. What TCP Ports are open?
3. How many UDP Ports are open?
4. What port is running a Metasploitable Root Shell?
5. What non-standard port is FTP running on?
6. What version of FTP is running on the non-standard port?

## Solutions:
<br>

##### Question 1: Which company created Metasploit?
<br>

Rapid7
<br><br>

##### Question 2: What TCP Ports are open?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To find the open TCP Ports, we can use `nmap -sT [IP]`. This shows us there are 23 open ports.
<br>

![img-description](/assets/img/posts/MS2IMG1.png)
<br><br>

##### Question 3: How many UDP Ports are open?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;To check how many UDP Ports are open, we can use `nmap -sU [IP]`. Using this we can see there are 7 open UDP Ports.
<br>

![img-description](/assets/img/posts/MS2IMG2.png)
<br><br>

##### Question 4: What port is running a Metasploitable Root Shell?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;We can use `nmap -sV [IP]` and look through the results to see whcih one is running the root shell. Here we can see it is running on port 1524.
<br>

![img-description](/assets/img/posts/MS2IMG3.png)
<br><br>

##### Question 5: What non-standard port is FTP running on?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;In the same scan from the previous question, we can see there is an FTP service running on port 2121 which is a non-standard port for FTP.
<br>

![img-description](/assets/img/posts/MS2IMG4.png)
<br><br>

##### Question 6: What version of FTP is running on the non-standard port?
<br>

&nbsp;&nbsp;&nbsp;&nbsp;We can use `nmap -sV -p 2121 [IP]` to get more information on port 2121 specifically since we know that is the non-standard port running FTP. Here we can see itis running ProFTPD 1.3.1.
<br>

![img-description](/assets/img/posts/MS2IMG5.png)
<br><br>
