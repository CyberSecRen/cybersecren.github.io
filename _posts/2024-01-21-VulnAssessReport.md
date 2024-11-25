---
layout: post
title:  "Simulated Vulnerability Assessment Report"
summary: "Using a Simulated Scenario to Create a Vulnerability Assessment Report"
author: Renato Ferreira
date: '2024-01-21 14:35:23 +0530'
category: Vulnerability
thumbnail: /assets/img/posts/VulnThumbnail.jpg
keywords: Vulnerability, report, assessment, framework
permalink: /blog/vulnreport/
usemathjax: true
---

<br><br>

# Simulated Vulnerability Assessment Report
<br>

## System Description
<br>

&nbsp;&nbsp;&nbsp;&nbsp;The server hardware consists of a powerful CPU processor and 128GB of memory. It runs on the latest version of the Linux operating system and hosts a MySQL database management system. It is configured with a stable network connection using IPv4 addresses and interacts with other servers on the network. Security measures include SSL/TLS encrypted connections.
<br><br>

## Scope
<br>

&nbsp;&nbsp;&nbsp;&nbsp;The scope of this vulnerability assessment relates to the current access controls of the system. The assessment will cover a period of three months, from June 2023 to August 2023. NIST SP 800-30 Rev. 1 is used to guide the risk analysis of the information system.
<br><br>

## Purpose
<br>

- How is the database server valuable to the business?
- Why is it important for the business to secure the data on the server?
- How might the server impact the business if it were disabled?

&nbsp;&nbsp;&nbsp;&nbsp;The database server is an integral part of the business and its ability to operate. Due to the employees being largely remote, it is important that they can access the database from where they are in order to access customer information in order to do business. The company being an e-commerce company means that all of the records are digital and payments are also made online which means they must comply with a variety of regulations that relate to such business practices. Having the server shutdown would mean that business can no longer go on until the database is running and secure.
<br><br>

## Risk Assessment
<br>

![img-description](/assets/img/posts/VulnAssessmentChart.png)
<br><br>

## Approach
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Risks considered in the data storage and management methods of the business. The likelihood of a threat occurrence and the impact of these potential events were weighed against the risks to day-to-day operational needs. A competitor may choose to take customer information in order to compete for the same customers as this company which could result in a decrease in the money the business is able to generate and can also expose the customers’ information to a company they did not agree to have their information shown to which may also harm reputation. A malicious hacker may use the database in order to find customer information due to it being public and thus an easy target. A malicious actor may also use the public database in order to gain access to the rest of the system and even possibly access credit card information which would put the customers at risk as well as the company’s reputation. Lastly, a disgruntled employee could look to use the customer database in order to sabotage the company, even if they no longer work there since the database is public. This could be anything from changing and/or removing customer information to using the information to contact customers to turn them away from the business or promote a competitor.
<br><br>

## Remediation Strategy
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Implementation of authentication, authorization, and auditing mechanisms to ensure that only authorized users access the database server. This includes using strong passwords, role-based access controls, multi-factor authentication to limit user privileges. Encryption of data in motion using TLS instead of SSL. IP allow-listing to corporate offices to prevent random users from the internet from connecting to the database. Limiting the ability to change and remove the information for the database would improve the chances of the information staying safe and correct so that even if a threat actor is able to access the database, their impact would be minimized if they do not have elevated privileges. Requiring a secure login with MFA would also prevent people from accessing the database if they are able to acquire login credentials.
<br><br>