---
layout: post
title:  "Leveraging OSINT Tools for Intelligence Gathering"
summary: "Using OSINT in Simulated Scenario"
author: Renato Ferreira
date: '2024-11-20 14:35:23 +0530'
category: OSINT
thumbnail: /assets/img/posts/OSINTThumbnail.png
keywords: open-source, intelligence, osint, simulation
permalink: /blog/osint/
usemathjax: true
---

<br><br>

# OSINT Intelligence Gathering Simulation
<br><br>
This exercise was provided by Security Blue Team for their Blue Team Junior Analyst certification.
<br><br>

## Scenario
<br>

&nbsp;&nbsp;&nbsp;&nbsp;You work for a law enforcement organization, and you have been assigned to track a person-of-interest, that is believed to be associated with a hacking group that recently compromised a Managed Service Provider (MSP) and are trying to sell the stolen credentials on both the clear net and dark web. Another team is focusing on the dark web lead, so you have been tasked with using OSINT sources to build up a profile on the individual and attempt to locate any evidence that links them to the MSP breach and sale of account details. You have been provided with some information to start your investigation. You should use any of the sources or tools taught in this course, that you deem to be applicable and appropriate. We know that the email address used to register the Twitter account is fake, so do not include this in your report.
<br>

#### Known Info:

Twitter Handle: @sp1ritfyre

#### Required Info:

1. First Name: 
2. Last Name: 
3. Age:
4. Country:
5. Interests (5 minimum):
6. Hacker's employer (company name): 
7. Hacker's position within company:
8. Self-Owned Website (Hacker owns the domain): Redhunt.net
9. Other Websites (Person does not own the domain, such as blogs):
10. Email Addresse Utilised:
<br><br>

## Solutions:
<br>

I began the investigation by looking at @sp1ritfyre’s twitter account. There was a link in the bio but this did not lead me anywhere and so I began by doing a google search for the same handle. The twitter profile had posted this lightbulb photo to their feed which matches this profile photo for a blogger user by the same name which points to the fact they are related. 
<br>

![img-description](/assets/img/posts/OSINTIMG1.png)
<br><br>

It appears the hacker is female and hovering over the email link we can see her email is d1ved33p@gmail.com. 
<br>

![img-description](/assets/img/posts/OSINTIMG2.png)
<br><br>

When searching for her handle, I also found a website called `redhunt.net` which my browser immediately warned me of being malicious and after visiting the website, there was no useful information aside from the fact that it was clearly attempting to steal information. The contact us section was password protected, which I assume is meant to attempt to steal your password and much of the website text is unfinished and in latin.
<br>

![img-description](/assets/img/posts/OSINTIMG8.png)
<br><br>

I did a google search for this email to see if any other accounts would appear and I got a result to SamWoodSecurity which appears to belong to the hacker because she writes that her personal email is the one we searched for. This website has her profile photo and a bio which says that her name is Sammie Woods.
<br>

![img-description](/assets/img/posts/OSINTIMG3.png)
<br><br>

Clicking on the “View my complete profile” link brings us to a page that has a whole host of information on her. Here we can see her location, her occupation, interests and more.
<br>

![img-description](/assets/img/posts/OSINTIMG4.png)
<br><br>

If we go into her archived blogs, specifically the first one, we can see Sam is 23 years old at the time of writing that blog. In this same post, she also mentions she works at PhilmanSecurityInc as a Junior Pentester.
<br>

![img-description](/assets/img/posts/OSINTIMG5.png)
<br>

![img-description](/assets/img/posts/OSINTIMG6.png)
<br><br>

Finally, to see if I could find any other information, I ran a whois lookup for redhunt.net and attempted to find the email associated with that domain by attempting to contact the domain holder on GoDaddy but due to recent privacy law changes, they do not show the domain holder’s email.
<br>

![img-description](/assets/img/posts/OSINTIMG7.png)
<br><br>

We now have all the info required to fill out the request we received.
<br>

#### Required Info:

1. First Name: `Sammie`
2. Last Name: `Woods`
3. Age: `23`
4. Country: `Reading, UK`
5. Interests (5 minimum): `Security, Programming, Technology, Gaming, Photography, Camping`
6. Hacker's employer (company name): `PhilmanSecurityInc`
7. Hacker's position within company: `Junior Pentester`
8. Self-Owned Website (Hacker owns the domain): `Redhunt.net`
9. Other Websites (Person does not own the domain, such as blogs):  
`https://sammiewoodsec.blogspot.com/`  
`https://sp1ritfyrehackerstories.blogspot.com/`  
`https://github.com/SammieWoodSec/Disrupt0r`  
10. Email Address Utilised: `d1ved33p@gmail.com`
<br><br>