---
title: Purchasing
permalink: /common-questions/purchasing/
---

# Purchasing Information

## What is an Apex Unit (AU) ?

Refer to the Specifications Section in About APEX.

---

## Are the Apex Unit (AU) based on per agency or per project?

It can be either.

---

## Can different projects be lumped into one AU?

Yes. It is possible for different projects of the same agency to use the same subscription.

---

## What is the difference between dedicated and shared AU?

A dedicated AU means that the full AU's resources belongs entirely to a subscriber, and performance will not be compromised by other projects usage in Apex.

For a Shared AU model, the resources will be distributed among the three shared projects, and AU's resources will not be guarantee to be distributed evenly if there are high consumption among one of the projects.

---

## For which period is the early adopter price applicable?

For new projects: any project that is subscribed before July 1 and on-boarded from now until Dec 2017.

For GWS-X migration projects: any project subscribed before July 1 and on-boarded in Wave 1 or Wave 2.

Note that scaling up or down the Apex Units after July 1 will revert the price to the original amount.

---

## How much does it cost to subscribe Apex?

The cost will vary depending on whether the account is a dedicated or shared service (only offered to existing GWSX users with low usage). Agencies can purchase a dedicated or shared service depending on the network traffic and their budget. A dedicated service costs more as compared to a shared service.

Contact the Apex Team for the price list.

---

## How many Apex Units (AU) would i need for my API?

The number of Apex Units (AUs) that you need will depend on the payload of the API and the number of concurrent calls.

The standard sizing guide for 1 AU are as follow :

|                          | REST API | SOAP API |
| ------------------------ | -------- | -------- |
| Peak TPS                 | 20       | 10       |
| API Calls Per Month      | 500,000  | 250,000  |
| Peak Data Size (kB)      | 50       | 100      |
| Average Data Size (kB)   | 20       | 40       |
| Bandwidth Reserve (Mbps) | 1        | 1        |

---

## If I am an existing user of GWSX and my API usage is low, can i have a better pricing plan? 

Yes, in case you expect low usage of the service, Apex provides a shared model service. Contact the Apex Team for the price list.

---

## How do I come on-board APEX?

Agencies would be required to sign a Service Agreement (SA). Interested agencies can contact the Apex Team.

---

## When will APEX start charging agencies?

APEX will only start charging an agency when it starts to on-board.

---

## Will there be any refund for APEX Units (AUs) subscribed but not used?

The billing will be based on the AUs subscribed and any unused capacity will NOT be refunded. Agencies can however request to scale down the AUs at least 1 month before the next billing cycle. For your information, Apex billing cycle is on a quarterly basis.

---

## How would i get billed?

Agencies will receive an electronic invoice on a quarterly basis. Payment must be made in advance at the beginning of each quarter.

---

## Does APEX support file transfer?

APEX does not support file transfers. Agencies will need to look for alternative solutions.

---

## Will there be any extra charges for agencies using beyond their subscribed APEX Units (AUs)?

The billing will be based on the AUs subscribed. Agencies who under-subscribe their required AUs will face a reduction in performance. GovTech will recommend agencies who under-subscribe their AUs to scale up based on the usage reports generated.

---

## Will there be preferential pricing for subscribing to more APEX Units (AUs)?

APEX currently works on a cost recovery model. There is no preferential pricing for larger subscribers now.

---

## What is the minimum contract period?

The minimum contractual term is 6 months.

---

## Can agency combine projects into a single Apex subscription?

This is not encouraged as it will bring about complexity in the administration for approving Consumer subscriptions (unless authorisation is done centrally).

Moreover, there will not be API isolation between different projects. (If an API is taking a lot of resources from the gateway, it might slow down another API from other projects.)

---

## What is the lead time to be on-boarded with Apex upon the signing of the Service Agreement?

It will take approximately 2-3 weeks to prepare the AU resource on top of opening up of firewall rules.

---

## My project is not a GWS-X migration project. Do I still need to wait until July 1 to onboard to Apex?

New projects can onboard to Apex at any time and do not need to wait until July 1.

Only GWS-X project will be on-boarded from 1 July in four waves.

---

## Will the API Consumer be charged?

In the current pricing model, the API Consumer will not be charged.

---

## How flexible is it to convert from shared to dedicated Apex Unit?

To change your subscription from shared to dedicated, please contact the Apex Team.

---

## Will it be necessary to purchase Production and UAT gateways separately?

It is highly recommended to buy purchase 2 separate gateways for UAT and production. This will isolate performance impact between production and UAT gateways.

---
