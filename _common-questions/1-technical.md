---
title: Contact Us
permalink: /common-questions/technical/
---

# Technical Information

## What protocols are supported for Apex?

Currently Apex supports REST API and SOAP web services. REST is the recommended method as it is more efficient, faster and easier as compared to SOAP.

---

## How do I create a staging environment for my API on Apex?

Both the staging and production environments are hosted on the Government Data Centre (GDC). Staging and production environments can be treated as different tenants. Agencies can purchase separate Apex units to create a staging environment. For details, contact the Apex Team.

---

## Does Apex include Content Delivery Network (CDN) for my application?

No, Apex does not provide Content Delivery Network (CDN).

---

## Can I create my API on Apex from a swagger file?

Yes, you can create an API on Apex from a swagger file. In fact, swagger is the recommended format, even though Apex also supports RAML (RESTful API Modelling Language) and WSDL (Web Services Description Language) formats.

## How can I leverage on the Cross-Zone Deep-Packet Inspection within Apex?

The payload cannot be encrypted to leverage on the DPI.

---

## To use Apex, do i need to host my application in Nectar?

Applications need not be hosted on Nectar to leverage on Apex.

---

## Is it possible to store files that can service request on Apex?

Apex is not meant for storing files. The provider of these files will need to expose it as a web service which can be fronted by Apex.

## Is there a limit on the number of consumers ?

There is no limit to the number of consumer that can use an API although we recommended to scale the number of Apex Units (AUs) per three application consumers.

---

## Is Apex a two-way or one-way API gateway?

Apex is a two-way API Gateway.

---

## Are the APEX Units (AUs) based on per agency per project?

AU can be based on agency or project.

---

## Can the API Provider be on the Internet?

There are two zones where the Apex services are hosted - Intranet and Internet. Depending on the sensitivity of the data, the API Provider can use either the Internet or the Internet zone.

---

## Is there any disaster recovery for Apex?

Keeping in mind the security and compliance requirements, there is no suitable disaster recovery site available for the current phase on which Apex can be deployed. This will change once a suitable hosting site becomes available.

---

## If there is a surge in the traffic, is there a process to scale up the Apex Units immediately?

It may take two weeks to spin up additional Apex Units. Subject to schedule availability.

---

## What is application layer security that the API Provider can implement to secure their API?

Apex supports two type of API authentication. For L1 it is APP ID and APP Secret , and L2 is certificate-based signing. We recommend L2 authentication for non-government consumers such as banks or business.

---

## Do I need two sets of APEX Units if there is both Intranet and Internet transactions (ie. to bridge across the gap)?

Yes, you will need two sets of AUs, one each for both Intranet and Internet segment.

---

## The 20 TPS is based on which level of the application?

Agencies will be able to do 20 requests per second for average 20 kB (peak at 50 kB) payload of REST API. This is the gateway performance, but there are other factors that can affect performance (ie. latency and bandwidth limits of the network or data processing speed at the application level). This is a theoretical performance based on ideal set-ups.

---

## For agencies that require more than 20 TPS, do they have to subscribe more?

Yes, agency can scale up more AUs if they need higher throughput.

---

## Does the TPS change if the payload size gets higher than 50 kB?

Yes. Higher the payload, lower the TPS.

---

## What is the maximum payload size?

Our recommended maximum payload size is 2.5 MB. However, due to the 1Mbps bandwidth allocated to each AU, it will take a long time to transfer and may cause a timeout.

---

## What is the Time-to-Live (TTL) for a caching mechanism?

The expiry is set to 5 mins.

---

## How can caching be handled for frequently fetched data?

Please contact the Apex Team directly for a discussion to activate such features.

---

## Are wave assignments by projects or by agencies?

Migration waves are based on projects.

---

## Are the certificates similar to GWS-X?

Yes, the certificates are similar. Subsequently, you can refer to [Learn - Essentials - Preparation](/learning-essentials/preparation/) for more information.

---

## What are the certificates agencies need to purchase?

Please refer to [Learn - Essentials - Preparation](/learning-essentials/preparation/) on the type of trusted certificates needed.

---

## Does Apex support transformation between REST and SOAP?

Data transformation should be handle at the source for performance reasons, however, Apex support data transformation through custom scripting available in Apex Community Manager. The scripts will be develop and maintain by the API provider.

---

## Does Apex support API orchestration?

It is not recommended to use API orchestration for production systems due to performance reasons. Support does not cover the usage of API orchestration.

---

## Is there a development environment available for Apex?

Agencies can subscribe to the staging instance on the production environment.

---

## Is OAuth supported in Apex?

OAuth is currently not support by Apex. It might possibly be a common feature in the near future if the demand is high.

---

## What are the differences between staging and production Apex's instance?

Production has High Availability (HA), while staging does not.

---

## What is a typical data flow with authentication in the Apex setup?

**Apex to API Provider** – One-way or Two-way transport layer security through SSL.

**API Consumer to Apex** – One-way transport layer security through SSL with application layer security with Application ID (L1) or certificate with PKI (L2).

---

## What firewalls do i need to open?

Please refer to [Learn - Essentials - Preparation](/learning-essentials/preparation/) for more information.

---

## Does Apex comes with High-Availability (HA)?

High Availability (HA) available for production Apex Units (AUs) only. For Staging AUs, HA is not available.

---

## Is there a tool to monitor if an APEX Unit is performing to what is intended?

Yes, agencies can monitor usage via the self-service APEX portal.

---

## Will an outsourced vendor be able to manage APEX through the self-service portal?

Yes, the data provider agency can decide whether to grant their outsourced vendor access to their APEX accounts. However, APEX administration can only be done through SGNet connectivity. Throttling is manage by GovTech for now. You may contact the Apex Team to help you with this.

---

## How are external entities , such as Business or Banks, subscribe to the government APIs?

APIs are fronted by GovTech. Private entities such as banks do NOT have access to the APEX portal, as it is only accessible through SGNet connectivity.

---

## What is a FQDN (Fully Qualified Domain Name)?

A FQDN is the domain name part of a URL (Unifrom Resource Locator) string that specifies it exact location in the tree hierarchy of the Domain Name System (DNS).

![fqdn](/images/common-questions/fqdn.jpeg "FQDN")

---
