---
title: Onboarding
permalink: /onboarding/onboarding/
---

# Introduction

These guides provide a brief overview of APEX and the necessary for our agency partners to get on-boarded with us. The intended audience for these guides are our Agency Partners and Developers that have no prior experience in using an API Gateway.

| API Providers | API Consumers |
| ------------- | ------------- |
| The back-end resource provider that expose or serve the respective function. | The client that consumes APIs. |
| To find out more about the provider workflow, please click here. | To find out more about the consumer workflow, please click here. |
| You may also download the detailed guide for providers here. | You may also download the detailed guide for consumers here. |

---

## What is an API?

A set of functions that allow the creation of applications which access the features or data from a Resource Provider.

---

## What is a APP?

A logical collection of APIs, and allow you to use a single access token to invoke a collection of APIs and to subscribe to one API multiple times with different SLA levels.

---

# API Preparation and Essentials

This section served as an elaboration of the steps, and other miscellaneous information that might be of interest. It will give everyone a good idea on what are needed to prepare before coming into APEX.

## API Definition Language

The APEX platform supports the following API definition languages.

| Definition Language | API Standard | Link |
| ------------------- | ------------ | ---- |
| Swagger             | REST | <http://swagger.io/specification/> |
| RAML                | REST | <http://raml.org/> |
| WSDL                | SOAP | <https://www.w3.org/TR/wsdl> |
| WADL                | SOAP | <https://wadl.java.net/> |

---

## API Interface Standards

APEX only supports the HTTPS standard on all incoming and outgoing connections. The API standards that we support are REST and SOAP.

---

## API Performance Considerations

APEX is designed for quick real-time information exchange; it is not suitable for services with intensive transactions or huge data extraction.

Thus, there is a limit on the data size per transaction. The recommended API data size is approximately **20-50 kB per transaction**, up to a **maximum of 2.5 MB**.

---

## API Security

### Transport Level Security Policy

Inbound and outbound traffic are handled by a dedicated F5 proxy situated between the client and APEX platform. The recommended version of TLS is 1.2. The table below shows the communication flow between the client and APEX.

| Communication Hop                        | Traffic  | TLS     | Certificate Type |
| ---------------------------------------- | -------- | ------- | ---------------- |
| Client (Internet / Intranet) to F5 Proxy | Incoming | One-Way | Public |
| F5 Proxy to APEX                         | Incoming | One-Way | Self-Signed Internal |
| APEX to F5 Proxy                         | Outgoing | One-Way | Self-Signed Internal |
| F5 Proxy to Client (Internet / Intranet) | Outgoing | One-Way | Public |

### Application Level Security Policy

The table below shows the application level security policies supported by APEX.

| Akana Security Policy Hop                | Algorithm       | Private Key Signing | APP ID | APP Secret | API Standards | GWSX Equivalent |
| ---------------------------------------- | --------------- | ------------------- | ------ | ---------- | ------------- | --------------- |
| API Consumer Application Security Policy | None            | No  | Yes | No  | REST | L1 |
| API Consumer Application Security Policy | SHA256 with RSA | Yes | Yes | No  | REST | L2 |
| WSS Security - Username Token            | N.A.            | No  | Yes | Yes | SOAP | L1 |
| WSS Security - X.509 Profile             | N.A.            | Yes | No  | No  | SOAP | L2 |

---

## Public Key Certificate Essentials

### Public Key Certificates Types

There are two types of certificates to be aware of, Root Certificate and Intermediate Certificate.

| Certificate Type | Description |
| ---------------- | ----------- |
| Root Certificate | It is a certificate issued by a trusted certificate authority (CA), and it served as a trust anchor that signed all the downstream certificates. This will be required to be shared with APEX team so as to import into the APEX trusted store so as to ensure secure connection is established. |
| Intermediate Certificate | This is required to be share with APEX team if there are use cases to verify a certificate authenticity through a chain of trust. |

### Public Key Certificate Format

You might need to prepare the following certificate formats before onboarding with us.

| Format | Mandatory | Purpose |
| ------ | --------- | ------- |
| .cer   | Yes       | Required by APEX to be able to trust your API endpoint (self-signed certificates are prohibited). Also required by your APP for API request verification (depending on the chosen API security policy - mainly for WSS Security X.509 Profile, SHA256 with RSA and HMAC with RSA). |
| .pfx   | No        | For importing into APEX's Community Manager Test Client. |
| .p12   | No        | For importing into APEX's Community Manager Test Client. |
| .pem   | No        | For you own client testing. Private key to sign your API request authorisation header. Specific to Node.js Crypto library. |
| .jks   | No        | To import keys and a certificate that has been issued by a third party Certificate Authority. |

### Recommended Trusted Root Certificate Authority

Below you will find a list of our recommended certificate authorities.

| Certificate Authority | Link |
| --------------------- | ---- |
| digiCert              | <https://www.digicert.com/digicert-root-certificates.htm> |
| Entrust               | <https://www.entrust.com/> |
| Comodo/Sectigo        | <https://www.comodo.com/> / <https://www.sectigo.com> |
| Verisign              | <https://www.verisign.com/> |
| GlobalSign            | <https://www.globalsign.com/en-sg> |
| GeoTrust              | <https://www.geotrust.com/> |
| NeTrust               | <https://www.netrust.net/> |
| Thawte                | <http://thawte.com/> |
| SGCore (Intranet only) | <https://sgcore-portal.sgnet.gov.sg/indexSR.html> |

---

## Infrastructure Preparation

### Transport Layer Security

Your system need to enable TLS version 1.2 so as to establish a secure communication channel between APEX and your system.

### X.509 Server Certificate

Ensure your system hostnames are registered with a public certificate authority so as to allow APEX to establish a connection to your system.

### X.509 Signing Certificate

Optionally, to prepare for API authentication through PKI (Public Key Infrastructure) signing, please prepare a X.509 certificate (2048 key length or above) signed by a public root certificate.

Do speak with the APEX team for more information as you may required assistance to import both Root CA and intermediate certificates.

### Firewall Rules Implementation

For API Producer, please raise a firewall rule request so that APEX incoming traffic can interface with your API endpoints. Additionally, please provide APEX team your endpoints IP address for sanity connection check.

For API Consumer, please raise a firewall rule request, depending on your internet network setup, so that your client can interface with APEX.

### Network Connection and Firewall Policies

   Opening of firewall is required for APEX depending on the agency hosting location
   
   APEX is hosted in GDC2
   
   Playload is subject to deep packet inspection, application layer will need to handle security incident

---
