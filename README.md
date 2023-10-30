<h1 align="center">
 Reliability Project
</h1>

<p align="center">
  This project is a Reliability Project, completed as part of Makers Academy Bootcamp during Week 7 & 8 of the Cloud/DevOps Engineering stream.
</p>

## 🎥 Demo Day oand Presentation

[Demo Day Video](https://youtu.be/XLbIx-UmkZY?si=G-QV16Xj--54PG45&t=2400)<br>
[Slides](https://docs.google.com/presentation/d/1amX-0ldebGgqnS9o0RDahwf0Znf59SYq06b_S-MdsrI/edit?usp=sharing)

## 🤝 Our Team
* **[Andrew Shakespeare](https://github.com/shakey0)**
* **[Benedict Valuks](https://github.com/BValuks)**
* **[Carolina Nogueira](https://github.com/caronog)**
* **[Denise Chan](https://github.com/elliepriestley)**
* **[Zubayda Hagi](https://github.com/Zhagi)**

## ❓ The Problem

We were tasked to work for a veterinary hospital client's HOSP system where we were asked to:
* Preserve the functionality of the system
* Increase the reliability of the system and ensure no security breaches
* Implement some improvements to the system

![Vet Diagram](images/vet_diagram.png)

## Constraints and Access
* **We only had access to the Load Balancer**
* We could submit tickets to HOSP or Corporate IT


## 🎯 Our Reliability Target

* The system responds to 99% of user requests successfully
* Ensure no security breaches

## Getting Visibility 

* Set up an S3 bucket to get logs from the Load Balancer
* Use Athena on AWS to query the logs

![Load Balancer Logs](images/setting_up_logs.png)

## Findings

* Saw the we had a fair amount of 5XX status codes
* Varying response times from 2 to 20 seconds

## Improving the Reliability of the System

### 1. Retry Mechanism

![Reverse Proxy Diagram](images/reverse_proxy_server.png)

Using a retry mechanism would allow for 5XX status codes to be go through the HOSP server up to a certain number of time, rather than just once.

This would increase the success rate of requests and improve the reliability of the system.

#### Set Up 
* Created Nginx Web Server on an EC2 Instance
* Set up a Reverse Proxy on the Nginx server
    * Allowed failed requests to retry up to 5 times
    * 3 seconds interval between each retry

<br>  

![Nginx Configuration](images/nginx_config.png)




