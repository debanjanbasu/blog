---
author: "Debanjan Basu"
title: "Personal Cloud Gaming Rig Setup"
date: "2021-01-18"
description: "Setup and configuration of AWS EC2 using terraform for cloud gaming"
tags: ["aws", "cloud", "gaming", "cyberpunk", "Australia", "4k"]
categories: ["gaming", "cloud", "aws"]
series: ["Cloud Gaming"]
aliases: ["setup-aws-cloud-instance"]
ShowToc: true
TocOpen: true
---

# The problem
During times of a pandemic, many have reverted to their desks at home not only for work, but also beyond it. All this started, as I tried to play CyberPunk 2077 🤖. Now, I'm not gamer, please don't judge me, but I do enjoy a good book, and sci-fi is my forte. So couldn't give this one a pass. The challenge was that I've quite a beefy rig, with 32GB DDR4 ram, and a 16-core XEON, with a measly Quadro k1200 😓. Even worse was trying on the [XBOX One X from last generation](https://support.cdprojektred.com/en/cyberpunk/xbox/sp-technical/issue/1763/my-game-crashes-8) constantly crashing.

☁ Cloud gaming has taken shape rapidly in 2020, behind the scenes with platforms such as Stadia, GeForce NOW, and even AWS launching [Luna](https://www.amazon.com/luna/landing-page). However, wide adoption is yet to be seen here in this subcontinent 🦘🪃, with us still relying on painfully slow NBN, and over expensive capped mobile 5G data. To add to the pain, the price of a relatively new GPU is to sell a kidney off, if they're even available in stores ! The Next-gen consoles, are all out of stock, and [scalpers](https://www.tomsguide.com/news/ps5-and-xbox-series-x-scalpers-ruining-restocks-what-you-can-do-now) are aiming for afr rich-list this year 💵.

# Solution
This post is about how we can use AWS to our rescue, and leverage gpu instances, albeit not originally designed for gaming, to the rescue. However, it wouldn't stop me from playing a game after almost a decade.

# Tools in my arsenal 🛠

## AWS G4dn EC2 Instance
[G4dn instances](https://aws.amazon.com/ec2/instance-types/g4/), `powered by NVIDIA T4 GPUs, are the lowest cost GPU-based instances in the cloud for machine learning inference and small scale training. They also provide high performance and are a cost-effective solution for graphics applications that are optimized for NVIDIA GPUs using NVIDIA libraries such as CUDA, CuDNN, and NVENC. They provide up to 8 NVIDIA T4 GPUs, 96 vCPUs, 100 Gbps networking, and 1.8 TB local NVMe-based SSD storage and are also available as bare metal instances.`

**Well Whatttt !!!**

From what I can say, the [T4 is half the performance of an RTX 2080](https://askgeek.io/en/gpus/vs/NVIDIA_GeForce-RTX-2080-vs-NVIDIA_Tesla-T4), still at the cost of the instances, it's a steal. Now the 2080 is not even remotely close to what I would love to have, i.e. a 3080/90, but at least ray tracing, and NVENC. I would come to the technical details of NVENC soon, and trust me it's important 🤔.

![AWS G4dn](images/g4dn-instances.png "AWS G4dn Instance Specs")

>These instances were clearly designed for machine learning, so I guess it's fair if they don't perform as amazing gaming rigs, spewing out unicorn vomit. But they still put out a fair fight, for the price, and no need to upgrade to a newer GPU/CPU/RAM every season.

![PCMR](https://media.giphy.com/media/p43Qy0rpMOSyCacZum/giphy.gif "Pc Master Race")

## Parsec
I guess there's no point to argue over the almighty [Linus Tech Tips, when he's using this for his team to edit LTT videos](https://www.youtube.com/watch?v=B821HqH-dWI). Shhhh... I'm a nerd, and not advocating for the almighty. But once a birdie referred to me as "Brown Anthony" 🤎, and actually I was super happy for it 😊.

{{< youtube B821HqH-dWI >}}
***
The amazing thing about Parsec is 