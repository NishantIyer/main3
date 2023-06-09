---
title: Portena - The Initial Idea
date: 2022-12-22T16:00:00Z
lang: en
duration: 9min
description: An idea i stumbled across.
---

# Portena: Revolutionizing Computing with Cloud-based Virtual Desktop Infrastructure

As a developer at Cardano, I monitor the High Performance Cloud market and provide cost-efficient ledgers. While monitoring one of the ledgers in Singapore, I wondered about the RAM and processing power required for a remote desktop connection. To my surprise, I found that it only needed around 10MB of RAM. This sparked the idea of Portena - a small single-board computer with 100MB RAM, a 1GHz processor, and an LTE modem that could connect to a cloud server and mirror its activities on a desktop screen using an HDMI/VGA cable. By renting and paying for only the required hourly basis computing power, we could avoid buying a full computer and quickly adjust the computing power as needed. This could indeed revolutionize computers as there would be no longer the need to own physical hardware and we could just rent the hardware.

Personal computing needs are very discrete, in that we sometimes use the CPU to its full capacity and sometimes only a fraction of it. Because CPU utilization varies every second, most computing power is wasted or idle for the majority of the time. This represents a waste of computing power. Furthermore, traditional PCs limit our computational ability because we cannot compute more than the available RAM or store more than the available storage space, which frequently results in lag and performance degradation. As a result, we are forced to update the hardware, which raises the cost.

Physical hardware increases the user's vulnerability to viruses, malware, and hacking, which can compromise personal and sensitive information.

"Every once in a while, a new technology, an old problem, and a big idea turn into an innovation," Dean Kamen once said. The time has come to think outside the box and reimagine computers.

Portena addresses all of these issues, including compute resource waste, costs, carbon footprint, and so on.

We would now like to provide a detailed overview of the technology, including its novelty, feasibility, and potential.

In the virtualization part, we have rented some of the instances from Alibaba Cloud and AWS to test the connectivity and billing models. We have also rented some OpenShift virtual desktop infrastructure for testing our own model of resource allocation, which we have developed.

## Portena's Elastic Allocation Model

Portena's Elastic Allocation Model utilizes a collective representation of RAM and balloon-like containers that can shrink and expand based on the user's needs. This approach is fundamentally different from the static resource allocation approach commonly used by cloud providers like AWS, where resources are allocated to users based on predefined units. With Portena, the use of containers allows for quick allocation and deallocation of resources, reducing costs and increasing efficiency. Additionally, Portena's pricing model is more sustainable and affordable for users, as they only pay for what they use on an hourly basis, as opposed to traditional computing models that require users to purchase or lease fixed hardware configurations regardless of their actual needs. For example, a server with a capacity of 32,000 GBs could easily serve over 1000 users, each with 32GB of RAM. In the scenario where user 1 uses 8GB of RAM, user 2 uses 12GB of RAM, and user 3 uses 12GB of RAM, they can all be accommodated in a single instance. This approach keeps other instances idle until the primary instance reaches its maximum capacity. By allowing each user to scale up to 32GB of RAM and distributing the load in an order-wise fashion, we can meet customer needs while conserving electricity and computing power.

## Payment System and Computational Credits

How will the user pay on an hourly basis? Won't it be a hassle?

Portena's app offers a simple and convenient payment system. Users can purchase computational credits in advance, and these credits are then used to pay for the hourly usage of the virtual desktop. This eliminates the need for users to make hourly payments and makes the process much more streamlined. Additionally, the use of computational credits allows for easier budgeting and cost control. Users can easily track their usage and remaining credits through the app, making it a hassle-free experience. For example, if a user purchases 100 computational credits, and each credit is worth 1 hour of computation time, then the user can use the computational resources for 100 hours. If the user only uses 50 hours, then they will have 50 credits left that they can use later. Using computational credits as a form of marketing can be an innovative approach to increase customer engagement and drive sales. For example, rewards for online purchases, referral programs, social media engagement, and loyalty programs. This will surely save the user tons of money, based on my research 60% cheaper.

## Portability and Potential Applications

One of the key advantages of Portena is its portability. Due to its small and minimal hardware requirements, Portena can be used on-the-go.

Portena's virtual computing concept has the potential to revolutionize not just traditional desktop computing, but also the mobile and wearable technology space. As more and more devices move towards thinner, lighter form factors, the need for hardware-based computing is decreasing. By leveraging cloud computing and virtualization technology, devices can now be designed to rely on remote computing power rather than local hardware. In the case of foldable phones, for instance, the flexible screen technology allows for a larger display area without increasing the size of the device. However, this can lead to limitations in terms of hardware capacity, particularly in terms of RAM and processing power. With Portena's virtual computing model, a foldable phone could rely on cloud computing to perform complex tasks while maintaining a slim form factor. Similarly, other wearables such as smartwatches or augmented reality glasses could benefit from Portena's technology. By relying on remote computing power, these devices could provide more advanced features without the need for bulky hardware. This could lead to a new era of wearable technology that is both sleek and powerful.

## The Potential of Portena

The potential of Portena is indeed enormous, especially with the imminent arrival of 5G technology. With 5G, the latency between the device and the cloud will be reduced to almost zero, making it possible to run applications in the cloud and stream them to devices in real-time without any noticeable lag. This makes Portena an ideal device for a variety of applications, ranging from education and gaming to business and personal use. Decentralized cloud computing can provide additional benefits in terms of security and privacy, as it allows for data to be stored and processed in a distributed network rather than in a centralized location. This can be done by locating servers every 1km all around the world. This can help to reduce the risk of data breaches or other security incidents, as well as providing greater control over who has access to sensitive data. Also, as everything is stored in secure state-of-the-art data centers, there is no possibility of a risk.

## Differentiation and Feasibility

There are several devices in the market, for example, the DaaS (Desktop-As-A-Service) offered by VMware and AWS for remote and hybrid work, and also the thin client which leverages the concept of cloud computing to provide PCs, but none of them have taken this approach to this level. For the past few months, we have been conducting a lot of market research, but to my surprise, I didn't find any similar products. Truly, Portena is completely novel and the first of its kind. Portena's feasibility can be evaluated from multiple perspectives. From a technical standpoint, the use of lightweight hardware and cloud-based virtual desktop infrastructure makes the system scalable and efficient. The elasticity and resource allocation model ensure that users only pay for the computing power they use, making it more cost-effective than traditional computing models. Moreover, the use of LTE modems in the hardware enables remote access to the virtual desktop from anywhere with internet connectivity. From a market perspective, Portena's model could be feasible due to its potential to disrupt the personal computing market. As more and more people turn to remote work and education, the need for affordable and flexible computing solutions is growing rapidly. Portena's model of computational credits and hourly payment can enable users to access computing power on-demand without having to worry about the upfront cost of buying a traditional computer. All we need for the remote connection is just 10 Mbps of stable network connection, which can be arranged easily nowadays. We are eagerly looking for mentors, investors, and incubators to bring my idea to fruition and incubate it into a successful company.

Thank You,

Regards,

Nishant Iyer
