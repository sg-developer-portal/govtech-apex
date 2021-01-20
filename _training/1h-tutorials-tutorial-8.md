---
title: Tutorial 8
permalink: /training/tutorials/tutorial-8
third_nav_title: Tutorials
---

# Tutorial 8: Conducting a Real-world Bridging API Test

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/fd7qYzfe8lUi" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

We have finished the setup of the source and proxy APIs throughout the tutorial series. Now we simulate a "real world" test by calling the proxy API using Node.js . We will be using Cloud9, an online IDE so you don’t have to install anything on your system. It’s all handled in browser.

## Step 1: Log in to the Cloud9 IDE

![login cloud9](/images/tutorial-8/1-login-cloud9.png "On Cloud9.")

Using that same login credentials that you got from the email, **login to Cloud9**. The username is just **providerXX** and the password is the same one used to log into the CMs.

## Step 2: Set up the Test Environment

![readme](/images/tutorial-8/2-readme.png "Open readme.")

So after logging in, we will be in the Cloud9 IDE. In the file browser on the left, **locate the readme.txt file and open it**. This contains terminal commands to create the required files and move into the folder to run the script. **Copy the text and paste it in the terminal window** below.

Let the magic work and you should find that a test helper folder has been created and that the terminal has been moved into it.

## Step 3: Upload Private Key to Testhelper folder

Now here’s an important part. You need to **upload your private key** that you’ve created in tutorial 6 to the cloud9 IDE. The test **requires** this key to access the proxy API that is using the L2 policy. Also you need to make sure that your private key filename is named properly according to the convention that we have specified. Otherwise, you’ll need to remember the convention you used. Without this key the test will fail.

## Step 4: Load the data.json File

### Bridging API L21
{
	"id" : "1",    
	"description" : "Bridging API L21.",    

	"authPrefix": "apex_l2_eg",    
	"realm" : "http://training.api.gov.gdshive.com",    
	"appId" : "app-id",    
	
	"invokeUrl" : "https://training.e.api.gov.gdshive.com/apex/team{XX}/v1/helloworld",    
	"signatureUrl" : "https://training.e.api.gov.gdshive.com/apex/team{XX}/v1/helloworld",    

	"httpMethod" : "GET",    
	"queryString" : { "clientname" : "{XX}.node.js.test.l2" },    

	"privateCertFileName" : "team{XX}.pem",    
	"privateCertFileType" : "pem",    

	"nextHop": {        
		"authPrefix": "apex_l1_ig",        
		"realm" : "http://training-pvt.api.gov.gdshive.com",        
		"appId" : "app-id",        
		"secret" : "app-secret",        

		"signatureUrl" : "https://training-pvt.i.api.gov.gdshive.com/apex/team{XX}/v1/helloworld",        
		"httpMethod" : "GET"    
	}
}

### Bridging API L12
{
	"id" : "2",    
	"description" : "Bridging API L12.",    

	"authPrefix": "apex_l1_eg",    
	"realm" : "http://client.com",    
	"appId" : "training-4Z1q0LxERCV4S5ZQzBpcoa7A",    
	"secret" : "3cc7463a9b616d595a3a9220a6d5da806b29b3c1",
		
	"invokeUrl" : "https://training.api.gov.gdshive.com/apex/team{XX}/v1/helloworld",    
	"signatureUrl" : "https://training.api.gov.gdshive.com/apex/team{XX}/v1/helloworld",    

	"httpMethod" : "GET",    
	"queryString" : { "clientname" : "{XX}.node.js.test.l2" },    

	   

	"nextHop": {        
		"authPrefix": "apex_l2_ig",
		"realm" : "http://client.com",
		"appId" : "training-pvt-AjvZR9xR7lC8NKyBjB0qSpSz",

		"signatureUrl" : "https://training-pvt.api.gov.gdshive.com/apex/team{XX}/v1/helloworld",        
		"httpMethod" : "GET",
		"privateCertFileName" : "team{XX}.pem",
		"privateCertFileType" : "pem"
	}
}

So after uploading, expand the test helper folder and **open the data.json** file. Now we need to open the written tutorial page and copy the Bridging API L21 and paste it into the .json file. This code chunk does an API call on the proxy API, which will then call the source API. This simulates a bridging API call from the internet to the intranet.

You’ll need to change a few things, namely the **app IDs, app secret, private key name, and the URLs**. The app IDs and secret should match the gateway that the code chunk calls. A quick way to tell is to read the *authprefix* property. If it says **EG**, it's for the proxy gateway, and if it says **IG** then it's for the source gateway. 

After updating the appropriate properties, **save the .json file**.

*Follow the same steps with the second code chunk to do the bridging API call L12. This is for the intranet to internet.*

## Step 5: Execute the Test

Now, move to the terminal and run the following command (**node index.js**). If you’ve followed the steps right the test should run and return with a 1/1 test clear.

## Common Mistakes

So if you don't get the test clear message in the terminal, here are some mistakes that you might encounter that will cause the test to fail.

The first would be that the endpoints for the APIs are *not configured properly or named correctly*. Follow the naming convention that we used in the tutorials and the endpoints should be configured properly. Or if you have changed the names for anything, make sure that you remember to use the correct names.

The second is usually a *wrongly named URL*.

So double check those two things mentioned and you should clear the test.

