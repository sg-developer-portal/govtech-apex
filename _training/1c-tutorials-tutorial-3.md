---
title: Tutorial 3
permalink: /training/tutorials/tutorial-3
third_nav_title: Tutorials
---

# Tutorial 3: How to create your first APP in APEX

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/8_M53KEZxDQ" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

With the API all locked up with the L1 authentication, we need a way of authenticating who can access our API. APEX does this in the form of APPs, which are a form of user identification. Since our API users are the consumers, this step is done from their (Consumer) perspective. So for people to access your APIs, they need to perform what is in this tutorial.

## Step 1: Login (yet again)

You should still be logged in to the internal (source/intranet) gateway. Since we don't have different account for different roles, we are reusing the provider account. There are some peculiarities with this setup, but this isn't always the case in production.

## Step 2: Create a new APP

![app create screen](/images/tutorial-3/1-app-create.png "App creation.")

Click on the big plus icon on the right side of the search bar at the top. Then click on "Add APP". This brings us into the APP creation screen. Here we can name our APP and add descriptors, as well as specify a App ID and Shared Secret. For our training purposes, fill in the entries on the left column (App name = Training Helloworld Team**XX** App, description, version, etc.). Leave the column on the right empty, especially the App ID and Shared Secret. These will be generated automatically.

## Step 3: Request Access to the API

![app access](/images/tutorial-3/2-access.png "App access.")

Now that we have our APP created, we can associate it with the API we want to access. The correct way is to search for the API that we want to access. On the overview page of the API, **click on the green Access button.**

![app inside](/images/tutorial-3/3-app-inside.png "App inside.")

We have to choose the APP that we want to associate with the API. In this case, we only have that one APP that was created not too long ago. **Click on the "Add" radio button** and then on Next. The next page lets us choose the environment that we want to deploy in. Here we only have the Live environment so choose that one and click Save.

This sends a request to the API Provider for them to approve. Once they have, the owner of the APP can activate the access and start using the API. And as you have guessed, we are both the owner of the API and the APP, so the request is essentially sent back to us. APEX will automatically approve it (Provider) and activate it (Consumer).

In reality this can take a while depending on the Provider. It's best to let the API Provider know that you want access to the API so that he/she can approve your access.

We have created an APP and linked it to our API, now it's time to test it. We will do it in the [next tutorial](/training/tutorials/tutorial-4).
