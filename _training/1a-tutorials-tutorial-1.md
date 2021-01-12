---
title: Tutorial 1
permalink: /training/tutorials/tutorial-1
third_nav_title: Tutorials
---

# Tutorial 1: How to create your first REST API in APEX

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/kSWJ5Rov9vE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

This is a first in the APEX Training tutorial series, where we will delve into the basics of APEX. This is mainly geared towards those who have signed up for our training course since our videos have been created in a custom environment, so some things may not be completely relevant. 

This tutorial will show you how to create a REST API using APEX's API Setup. After completing this tutorial, you should know how to create a REST API as well as do a test call of it.

## Step 1: Login to the source gateway

![login screen of apex](/images/tutorial-1/1-login.png "Login to the corect gateway!!")

We will be creating a REST API on the source gateway. The URL is:

<http://training-pvt.cm.gov.gdshive.com:9945/cm>

This gateway is the side of APEX that handles intranet traffic. **Please log in** using the e-mail and password provided to you. The e-mail format is: **providerXX@userad.idahive.sg**

## Step 2: Create a REST API

![apex portal homepage](images/tutorial-1/2-add-api.png "You'll be seeing this a lot.")

After logging in, find the giant plus icon at the top right of the screen next to the search bar. This button is what you will click on to create APIs and APPs. **Select Create API** from the drop-down menu.

### Creating an API

#### Add API

![create api screen](images/tutorial-1/3-add-api-page.png "Make APIs.")

Here we can specify how we want to create our API. The main methods are from scratch using our API Setup or by importing a file such as a SWAGGER/WSDL document. For our tutorials however, we'll be creating a REST API from scratch. So pick that option. **Specify a name for your API and use this URL for the endpoint:**

*https://sherlock.apex.gdshive.com/rest/api/helloworld*

This is a sample endpoint for your API to hit when it is called. Click Save to continue.
*Note that providers should whitelist their FQDNs through the APEX Portal when in production*

#### API Design Page

![api design page](images/tutorial-1/4-add-api-design.png "Complex stuff not needed now.")

We can structure the API functionality here. You can add other commands for the API to do other than GET. For this tutorial, we can just leave everything as default. **Click Save to continue.**

And you have finished creating your very first REST API in APEX. Your API is now "Live" and can be called. However, lets do some housekeeping first.

#### The API Implementation Page

![choose implementation](images/tutorial-1/5-implem.png "Choose the corect option.")

![pick the live implementation](images/tutorial-1/6-live.png "The only option available anyway.")

**Go to the API Implementation page (Implementation -> Live).** We want to make our APIs calculated endpoint easier on the eyes instead of the auto-populated mess given by APEX.

![implementation page](images/tutorial-1/7-deployments.png "Deployment.")

![implementation page edit](images/tutorial-1/8-context-path.png "Deployment .")

So in the deployments section, **click on the green Edit button** and replace the context path with:

/apex/team**XX**/v1/helloworld
*Replace the bold text with your team number*

This context path specifies the resource that you want your API to get. In this case, *helloworld* is the target resource that will be returned to the GET call.

And we're done with the API creation.

### Step 3: Testing the API

#### Test Client

![test client page](images/tutorial-1/9-test-client.png "Test Suite woo.")

No API creation would be complete without doing some tests. APEX comes with a powerful tool to conduct such tests called Test Client. This allows us to do an API call with many different parameters. Left to its defaults, it will do a GET call on the API and record the attempt in the call logs. **Click on Invoke to call your API.**

#### Call Logging

![Logs page](images/tutorial-1/10-logs.png "Not the un-environmental kind.")
*No trees were felled*

All API calls are logged by APEX. This way we can see what happens when the API is called. The caller, resource called, call status, .etc are all collected. **Go to Monitor -> Logs.** We can see that the API call was successful from the number in the status column. 200 in http code means that the call was successful.

#### The Audit function

In normal operation, Logs will only log the send and receive requests from the APEX server only. It does not log the server to resource interaction. In certain cases (usually troubleshooting) we want to see what goes on behind the API call. In cases like these, we can turn on a function called auditing.

##### What is auditing?

Auditing is a function you can turn on for the command you are calling on the API. It basically tells APEX to log the server/resource interactions in the API call. One of the use cases would be to check if APEX is calling the correct resource.

![where to find the process editor](images/tutorial-1/11-resources.png "Hard to find.")

**Go back to Implementation -> Live.** You should see a Resources section at the bottom of the page. At the only resource within, **click on the tiny drop-down arrow on the right.** That should bring you into the resource editor.

![process editor](images/tutorial-1/12-process-editor.png "Super complex potential.")

This is the place where you can create magic with your API calls. But for this tutorial, **click on the Invoke node.** This will bring up the Activity Details Wizard.

![turning auditing on](images/tutorial-1/13-act-wizard.png "Auditors are coming.")

We can turn on auditing by simply checking the Audit checkbox in the wizard. Once you've familiarised yourself more with APEX then you can play around with the other features. For now, **click Finish to close the wizard and Finish again to exit.** Now you can head back to the Test Client and invoke the API again to see the results.

![Before](images/tutorial-1/14-before.png "Before.")

![After](images/tutorial-1/15-after.png "After.")

Before, nothing would show up when we click on the magnifying glass on the server/resource side. Now, the body of the http send/repsonse will show up. This is how you know if auditing is turned on.

*Typically, auditing is turned off when in production to reduce the load on the servers. So don't leave it on when you deploy.*

With that, tutorial 1 is done. You may proceed on to the next tutorial which deals with the security of the API.
