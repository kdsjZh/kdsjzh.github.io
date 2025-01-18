---
permalink: /
title: "About Me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I'm a PhD Student at [HexHive@EPFL](https://hexhive.epfl.ch), advised by Prof. Mathias Payer.
I received my master degree in University of Chinese Academy of Science in 2023 and my bachelor in Xidian 
University in 2020. I'm broadly interested in Software and System security, particularly in Browser 
Security and Fuzzing. 

Besides the research, I actively contribute to open source community by submitting bug reports 
and intergrating my research prototypes. So far I reported more than 50 CVEs for 
widely used open source software and integrated my research prototypes in AFL++[1], 
one of the most widely used greybox fuzzing framework.

I enjoy bug hunting on complex software system for fun <del>and profits</del>. By 
leveraging static analysis, fuzzing and code auditing, I successfully found a 
series of vulnerbilities in web browsers and rank #42 in Google VRP 2024, 
receiving 25,000 USD bug bounties.

Selected Publication
======
<a id="1">[1]</a> MendelFuzz: The Return of the Deterministic Stage, ESEC/FSE'25

<a id="1">[2]</a> FishFuzz: Catch Deeper Bugs by Throwing Larger Nets, USENIX Sec'23


Bug Hunting
======

| Vendor           | Bug       | Severity  |                                                    |
| --------         | --------- | --------- | -------------------------------------------------- |
| ChromeOS         | b/385851796   | High   | Global-Buffer-Overflow in Virglrenderer             |
| Chrome           | CVE-2025-0438 | High   | Stack-Buffer-Overflow in Tracing                    |
| Chrome           | CVE-2025-0436 | High   | Integer Overflow in Skia                            |
| Chrome           | b/365802556   | High   | Use-After-Return in Blink                           |
| Chrome           | CVE-2024-7968 | High   | Use-After-Free in UI                                |
| Chrome           | b/351843813   | Medium | Use-After-Free in UI                                |
| Chrome           | CVE-2024-5847 | Medium | Use-After-Free in PDF                               |
| Chrome           | CVE-2024-5846 | Medium | Use-After-Free in PDF                               |
| Chrome           | CVE-2024-7018 | Medium | Heap-Buffer-Overflow in PDF                         |
| Wireshark        | CVE-2024-0210 | Unknown | DoS in Wireshark dissector                         |
| Wireshark        | CVE-2024-0209 | Unknown | DoS in Wireshark dissector                         |
| Apple            | CVE-2022-26981 | Unknown | Global-Buffer-Overflow in Font                    |
| Huawei           | CVE-2022-31783 | Unknown | Global-Buffer-Overflow in Font                    |




