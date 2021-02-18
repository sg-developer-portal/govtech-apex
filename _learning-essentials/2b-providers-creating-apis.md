---
title: Creating Apis
permalink: /learning-essentials/providers/creating-apis
third_nav_title: Providers
---

# Creating APIs

The steps below will give you a brief overview on what you will need to do in order to create a API.

For detailed steps download the guide for Providers.

> Note
> 
> You will have to be in the gateway page in order to start creating APIs

---

## STEP 1 - Create a New Entry

![turning auditing on](/images/tutorial-1/13-act-wizard.png "Auditors are coming.")

From the + (plus icon) at top menu, click on "Add API".

---

## STEP 2 - Design your API

From here you will have 2 options on how you want to create your API.

### Option 1 - Design an API from scratch (REST APIs only)

From the Add API screen, type a name in Name, optinally add a resource endpoint in Endpoint, and then click "Save".

![turning auditing on](/images/tutorial-1/13-act-wizard.png "Auditors are coming.")

### Option 2 - 

From the Add API screen, select "I have a Swagger/RAML/WSDL/WADL document" option. There are two options for you to import, through and online URL or upload the file directly. If your import is successful, you will be redirected to the respective API page.

For importing via online URL, please type in the document location in the URL field. You can leave the "Authentication Options" as default if you do not need privilege access to retrieve the document archive. Click "Save" to proceed.

![turning auditing on](/images/tutorial-1/13-act-wizard.png "Auditors are coming.")

For importing via uploading file, select the document and click "Upload". You should see the document name appeared in the "File" field, and click "Save" to proceed.

![turning auditing on](/images/tutorial-1/13-act-wizard.png "Auditors are coming.")

---

## STEP 3 - Update API Endpoints

To update the API endpoints into something more descriptive, please select "Details" from the left panel. Under the deployment section within the details page, select the endpoint that you want to update and click on "Edit".

![turning auditing on](/images/tutorial-1/13-act-wizard.png "Auditors are coming.")

---

## STEP 4 - Update Endpoint URL

To update the endpoint URL, type in the desired resource name in the "Context Path" field and click "Save" to proceed. You should see the endpoint updated, and ready for testing.

![turning auditing on](/images/tutorial-1/13-act-wizard.png "Auditors are coming.")

> **Important**
> 
> For SOAP APIs, please remember to import the WSDL directly from the Community Manager for your APP consumptions or local testing. Select the newly imported SOAP API. From the API's main screen, go to "Details", and right-click on the WSDL icon under implementation. Right-click and select "Save As" or "Save Link". Give the file a meaningful name and save it as a WSDL file.
