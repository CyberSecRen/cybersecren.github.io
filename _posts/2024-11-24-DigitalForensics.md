---
layout: post
title:  "Digital Forensics Scenario Simulation"
summary: "Using Digital Forensics Techniques to Conduct an Investigation"
author: Renato Ferreira
date: '2024-11-24 14:35:23 +0530'
category: Forensics
thumbnail: /assets/img/posts/ForensicsThumbnail.png
keywords: forensics, analysis, steganography, simulation, investigation
permalink: /blog/digforensics/
usemathjax: true
---

<br><br>

# Digital Forensics Simulated Scenario Activity
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Scenario:
<br>

&nbsp;&nbsp;&nbsp;&nbsp;The SOC has received an anonymous report that a user is potentially exfiltrating data from the company. An image of the user’s hard drive has been taken, and you are responsible for analyzing the contents of a perfect copy to find any evidence of malicious activity. Using your newly developed skills, search through the folders and files using techniques to uncover 4 pieces of hidden information (each piece of evidence will contain the string {1 of 4} or similar). You will be tested on your ability to discover this information using all of the techniques taught in this course; Linux CLI navigation, identifying incorrect file extensions, identifying hidden files/folders, steganography, and password cracking. You have been told that the most recent file on the hard-drive was an email file with an attachment in the “Saved Emails” directory. It is suggested you start there.
<br>

## Questions:

1. [Evidence 1/4] What is the name of the file where the evidence was found? (filename and extension)
2. [Evidence 1/4] What is the name of the directory you're in where this evidence was found?
3. [Evidence 2/4] What is the name of the file where the evidence was found? (filename and extension)
4. [Evidence 2/4] What is the name of the directory you're in where this evidence was found?
5. [Evidence 3/4] What is the name of the file where the evidence was found? (filename and extension)
6. [Evidence 3/4] What is the name of the directory you're in where this evidence was found?
7. [Evidence 4/4] What is the name of the file where the evidence was found? (filename and extension)
8. [Evidence 4/4] What is the name of the directory you're in where this evidence was found?

## Walkthrough:

&nbsp;&nbsp;&nbsp;&nbsp;We received the suggestion to begin in the Saved Emails section and so that is where I began my investigation. I started by checking the directory for any hidden directories using `ls -a`, since there were none, I began by reading the email file that was saved. This email file said that the Form1.jpg was attached and so I began by opening it to check if anything was filled out but nothing was and so I used the `cat` command just in case there was a hidden message and that’s what I found.
<br>

![img-description](/assets/img/posts/ForensicsIMG1.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG2.png)
<br><br>

&nbsp;&nbsp;&nbsp;&nbsp;Knowing that these usernames and passwords were hidden in a .jpg file, I went back to the Disk Image folder and into the Images folder. There were multiple .jpg files in this folder so I tried to extract the first one called exploratory.jpg. I used the password acquired from Form1.jpg but this didn’t work so I moved on to laptop.jpg. Using `steghide -sf laptop.jpg` a password file was extracted.
<br>

![img-description](/assets/img/posts/ForensicsIMG3.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG4.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG14.png)
<br><br>

&nbsp;&nbsp;&nbsp;&nbsp;While in this directory, I also wanted to make sure to check if all the files matched what their extensions were. I tried this first on the “desk stock img.mp3” file using the file command. The result returned that it was actually a JPEG file and not an MP3 file.
<br>

![img-description](/assets/img/posts/ForensicsIMG5.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG6.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG7.png)
<br><br>

&nbsp;&nbsp;&nbsp;&nbsp;I began checking for hidden files or directories and investigating things as I came across them. While navigating the system, I found a file under Week 10 of the weekly meeting notes that was an xml file but using the file command, I found it was actually a png image. This png contained their office locations.
<br>

![img-description](/assets/img/posts/ForensicsIMG8.png)
<br>

&nbsp;&nbsp;&nbsp;&nbsp;As I kept searching, I went into the WebDev Work directory and under the unfinished webpages folder, I found a to-do folder that appeared empty. I looked for a hidden directory or file in there with ls -a and found a hidden .zip file.
<br>

![img-description](/assets/img/posts/ForensicsIMG9.png)
<br>

&nbsp;&nbsp;&nbsp;&nbsp;I attempted to unzip it but it requested a password. I used the rockyou.txt file to execute a dictionary attack for the password and it worked.
<br>

![img-description](/assets/img/posts/ForensicsIMG10.png)
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Now I can unzip the hidden file and find out what’s inside. This employeedump file has a ton of employee information on it.
<br>

![img-description](/assets/img/posts/ForensicsIMG11.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG12.png)
<br>

&nbsp;&nbsp;&nbsp;&nbsp;I continued to look around for the final piece of evidence when I came across a .abc file under the css directory in the templatemo_508_power folder which was under the unfinished webpages. Since this one was different from the others, I used `cat` to see if I could get any information from it. Here I found the final piece of evidence.
<br>

![img-description](/assets/img/posts/ForensicsIMG13.png)
<br><br>

##### Here is the evidence organized in order from 1-4:
<br>

![img-description](/assets/img/posts/ForensicsIMG12.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG14.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG8.png)
<br>

![img-description](/assets/img/posts/ForensicsIMG13.png)
<br><br>