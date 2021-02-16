---
title: Specifications
permalink: /getting-started/specifications/
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

