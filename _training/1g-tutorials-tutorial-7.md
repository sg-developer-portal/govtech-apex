---
title: Tutorial 7
permalink: /training/tutorials/tutorial-7
third_nav_title: Tutorials
---

# Tutorial 7: Enabling L2 Authentication for the Proxy API

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/vlLJRZP4vtg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

After all that work setting up the key-pairs in the last tutorial, we are finally ready to upgrade our security policy to L2.

We are assuming that you have followed the tutorial till this one, and so your intranet API **should not** have the L1 authentication policy attached yet. If it is, please remove it.

## Step 1: Attach the REST L2 Authentication Policy to the proxy API

![l2 policy](/images/tutorial-7/1-l2-attach.png "Attach the L2 policy.")

On the proxy/internet gateway, **attach the REST L2 Authentication Policy v2 - EG** to the proxy API. Remember to use the one for the external gateway (the one with **EG** at the back)

## Step 2: Test the L2 policy

### Set up the invoke command

This time we actually have to set up the invoke command properly. Go to the Test Client and **Click on Setup** to open the Setup dialog box.

### Upload Keystore file

![upload keystore](/images/tutorial-7/2-upload-keystore.png "Upload the Keystore file.")

In the dialog box, **check the Upload Keystore checkbox**. Locate the keystore file (**.p12**) and type "password" for the password.

### Invoke the proxy API

Now we can **invoke the API** and if nothing goes wrong we should get the HTTP status code 200. The proxy API is completely set up.

## Step 3: Re-attach the REST L1 Authentication Policy to the source API

Remember we removed the L1 policy from the source API way back? We need to re-attach it back. So **log back in to the source gateway** and re-attach the REST L1 Authentication Policy back to the source API.

Once that is done, the entire system can no longer be tested using APEX's Test Client. The bridging APIs are complete. If we wanted to test this system, we need to simulate a real situation where this API will be called. That will be done in the [next and final tutorial](/training/tutorials/tutorial-8) of this series.
