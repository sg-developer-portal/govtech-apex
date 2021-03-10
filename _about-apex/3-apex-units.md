---
title: APEX Units
permalink: /about-apex/apex-units/
---

# APEX Unit

APEX services are charged in terms of APEX Units (AUs). An APEX Unit is the resource used to process the incoming API request and each APEX Unit consists of:

* One CPU
* 4GB RAM

An APEX Unit can typically handle **20** TPS (Transaction Per Second) for REST and **10** TPS for SOAP API calls.

|                          | REST API | SOAP API |
| ------------------------ | -------- | -------- |
| Peak TPS                 | 20       | 10       |
| API Calls Per Month      | 500,000  | 250,000  |
| Peak Data Size (kB)      | 50       | 100      |
| Average Data Size (kB)   | 20       | 40       |
| Bandwidth Reserve (Mbps) | 1        | 1        |

# Guidelines to Estimate Amount of APEX Units Required

Digital services that make between 50,000 to 500,000 web-service transactions per year are encouraged to subscribe to 1 APEX Unit (AU). Each AU can take around 20 Transactions Per Second for an average of 20 kB (Kilobyte) payload of REST API calls (peak 50kB payload for short durations).

The number of AUs will double if agencies need cross zone (Internet and Intranet) services with similar usage.

|                          | REST API | SOAP API |
| ------------------------ | -------- | -------- |
| Peak TPS                 | 20       | 10       |
| API Calls Per Month      | 500,000  | 250,000  |
| Peak Data Size (kB)      | 50       | 100      |
| Average Data Size (kB)   | 20       | 40       |
| Bandwidth Reserve (Mbps) | 1        | 1        |

Use our AU Calculator [here](/training/tutorials/tutorial-5) to find out how many AUs you might need for your use case.
