---
title: Au Calculator
permalink: /getting-started/au-calculator/
---

# Guidelines to Estimate Amount of APEX Units Required

Digital services that make between 50,000 to 500,000 web-service transactions per year are encouraged to subscribe to 1 APEX Unit (AU). Each AU can take around 20 Transactions Per Second for an average of 20 kB (Kilobyte) payload of REST API calls (peak 50kB payload for short durations).

The number of AUs will double if agencies need cross zone (Internet and Intranet) services with similar usage.

## REST APIs
Peak TPS:                   20
API Calls Per Month:        500,000
Peak Data Size (kB):        50
Average Data Size (kB):     20
Bandwidth Reserve (Mbps):   1

## SOAP APIs
Peak TPS:                   10
API Calls Per Month:        250,000
Peak Data Size (kB):        100
Average Data Size (kB):     40
Bandwidth Reserve (Mbps):   1

Use our AU Calculator [here](/training/tutorials/tutorial-5) to find out how many AUs you might need for your use case.
