---
title: Tutorial 4
permalink: /training/tutorials/tutorial-4
third_nav_title: Tutorials
---

# Tutorial 4: Testing the API with the L1 Policy

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/lmouW-jB4D8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

This is a relatively short tutorial as compared to the others. We are doing an API call using the APP to authenticate us and tell APEX that we are authorised to access the API.

## Step 1: Navigate to the Test Client in the APP

![go to test client](/images/tutorial-4/1-test-client.png "Go to Test Client.")

Since it is the APP that allows us to access the API, we need to invoke the API call from the APP's perspective. This is done through the APP's Test Client. Go to the APP that we have created in the last tutorial. Then **click on the Test Client** on the left side.

## Step 2: Set up the Invoke Command

![set up invoke](/images/tutorial-4/2-setup.png "Set up Invoke.")

We need to set up the invoke command to use our APP as the identifying method to invoke the API call. Next to the Invoke and Security buttons there is a Setup button. **Click on it** to open the Setup Menu. Here we can check if the APP ID and Shared Secret are identical with the APP that we want to use. The values should be auto-populated by the system since it is only connected to one API. **Click Save** to continue.

## Step 3: Invoke the command

![invocation](/images/tutorial-4/3-invoke-cmd.png "Invocation.")

Now all that's left to do is to **hit the Invoke Button** and get the HTTP status code 200!

We've finished the full setup process for the intranet gateway of APEX. In tutorial 5 we will be doing the same process again, but we'll have to change the parameters to match the internet gateway that we will be using. Head on to the next tutorial to begin.
