---
title: Tutorial 5
permalink: /training/tutorials/tutorial-5
third_nav_title: Tutorials
---

# Tutorial 5: Setup the internet API and APP

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/5pnrvXLfKNI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

We've learnt how to setup an API and APP on the intranet gateway of APEX. Now we'll learn how to do the same on the internet gateway. If you didn't know by now, APEX has two different "sides", an intranet side, and an internet side. The intranet side is usually reserved for internal government use, and the internet side is usually used by agencies to expose their APIs to the public. If necessary, both sides can communicate through APEX in a bridging API call. This is the eventual end goal of this tutorial series.

However, since we have to deal with the internet, the requirements to create an API are different. The main difference in our tutorial will be the use of a different authentication system to verify users.

## Step 1: Log in to the proxy gateway

We are creating a new API in a new environment, the proxy gateway. This is the internet zone of APEX where we host APIs that can be accessed by the public. Please log in to the proxy gateway. The URL is as given:

<http://training.cm.gov.gdshive.com:9945/cm>

## Step 2: Create the proxy API (Tutorial 1)

Create an API in the same way that we did in tutorial 1. However, we are dealing with the internet/proxy gateway so we'll need to change some parameters to set up the bridging scenario. When we do an API call on the proxy API, it will then do another API call through APEX to the intranet/source gateway to hit the source API. Thus the *internet API's* **target endpoint** must be the *intranet API's* **calculated endpoint**.

![intra-inter-param](/images/tutorial-5/1-intra-inter.png "Intranet-internet parameters.")

| Attributes              | Intranet                       | Internet                       |
| APEX API Name           | Training Helloworld Team**XX** | Training Helloworld Team**XX** |
| Gateway Name            | training                       | training-pvt                   |
| Context                 | apex/team**XX**                | apex/team**XX**                |
| Version                 | v1                             | v1                             |
| Resource                | helloworld                     | helloworld                     |
| Sercurity Policy        | **REST L1 Authentication Policy v2 - IG** | **REST L2 Authentication Policy v2 - EG** |
| Target Endpoint URL     | https://sherlock.apex.gdshive.com/rest/api/helloworld | http://training-pvt.api.gov.gdshive.com/apex/team**XX**/v1/helloworld |
| Calculated Endpoint URL | http://training-pvt.api.gov.gdshive.com/apex/team**XX**/v1/helloworld | http://training-pvt.api.gov.gdshive.com/apex/team**XX**/v1/helloworld |

In the pictures above you'll find the different parameters for the internet or intranet APIs. The URL for the endpoints are built from **context** > **version** > **resource**.

## Step 3: Test the proxy API

![error pic](/images/tutorial-5/2-proxy-error.png "Error.")

We should always test our API/APP before continuing, so go to the test client and invoke the API. Boom. Password prompt. But this wasn't the case when we were creating APIs on the source gateway. We didn't even add any security policies to the API and we're getting this?

The reason that we're getting this prompt is that it's coming from the L1 authentication policy on the source API. The L1 policy restricts access to the API by unauthorised and unknown users. Here, the proxy API is currently unknown to the source API and thus cannot access it.

![remove l1 ploicy](/images/tutorial-5/3-remove-l1.png "Remove L1.")

We can remedy this by temporarily **removing the L1 authentication policy and allowing anonymous access** to the source API. Then we can do our test properly. We’ll re-enable this policy at the end of tutorial 7.

*Please make sure that you can invoke the API properly. This will save a lot of troubleshooting if there's anything wrong in the future.*

## Step 4: Attach the L1 Authentication Policy to the proxy API (Tutorial 2)

Attaching the L1 should'nt be an issue since it's all within the proxy gateway. Note that the environment is the proxy gateway so we need to use the **REST L1 Authentication Policy v2 - EG**. Also, don't forget to **uncheck anonymous access**. Test the API after attaching the policy. We are expecting a password prompt just like the one from eariler.

## Step 5: Create the proxy APP (Tutorial 3)

Just like in tutoral 3, we need to use an APP to access a L1 secured API. So **create an APP** for the proxy API and link it to the proxy API.

## Step 6: Test the proxy API using the APP (Tutorial 4)

Finally we can **test the entire system** from proxy to source. When the proxy API is invoked, it will then invoke the source API through APEX. This is the bridging API call that we are trying to simulate.

We're done with the entire system and APEX for now. In the next tutorial we will start to configure key-pairs to further enhance the security of the entire system.
