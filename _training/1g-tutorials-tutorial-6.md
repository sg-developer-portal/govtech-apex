---
title: Tutorial 6
permalink: /training/tutorials/tutorial-6
third_nav_title: Tutorials
---

# Tutorial 6: Generating key-pairs for L2 Authentication

<div class="youtube">
  
<iframe width="560" height="315" src="https://www.youtube.com/embed/vlLJRZP4vtg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
</div>

So far we’ve been using the L1 policy to control access to our APIs, but that’s not good enough for APIs exposed to the public. Attackers might obtain the APP ID and Secret and be able to access our L1 secured APIs. So for internet facing APIs, we will have to use a more secure form of authentication in the form of public-key cryptography (like RSA). This uses public-private key pairs to authenticate users.

In this tutorial we will use a program called Keystore Explorer (v5.2.2+) to generate the key-pairs required for the L2 authentication policy to secure our APIs. If you haven't installed Keystore Explorer yet, please do so now. The repository is at: <https://github.com/kaikramer/keystore-explorer/releases>

## Step 1: Create a new Keystore

### Keystore filetype

![Keystore explorer](/images/tutorial-6/1-create-keystore.png "Keystore Explorer.")

A keystore file is what contains the public and private keys. **Create a new keystore file**. Select the **PKCS#12** for the type.

### Set up the default values

![set up default values](/images/tutorial-6/2-set-defaults.png "Setting up of defaults.")

By setting up the defaults for some parameters, we can save time instead of re-typing each time we need to. Go to **KeyStore Explorer Menu > Preferences > Default Name**. Fill in the fields shown in the picture above.

### Generate the key-pair

![gen keypair](/images/tutorial-6/3-rsa.png "Generation of keypair.")

Click on the icon as shown above to generate a new Key-Pair, leaving the settings as the default values: **RSA with Key Size 2048**.

### Fill in the common name

![common name](/images/tutorial-6/4-common-name.png "Fill in the common name.")

Use your assigned team number as the common name in the format **teamXX**. Do the same for the Alias field and key in **password** for the password.

### Save the Keystore file

A new keystore file will be generated. **Press Ctrl+S (Cmd+S)** to save the KeyStore. Type in **password** for the password and append the keystore filetype to **.p12**.

## Step 2: Export the Certificate Signing Request (CSR)

![export csr](/images/tutorial-6/5-export-csr.png "Exporting the CSR.")

In order to use the key-pair, we must first generate a Certificate Signing Request (CSR). This request is for APEX to sign as the root L2 certificate authority to generate the server public certificate. This is then used to export the private certificate. The private certificate is the file that will identify the user. This cert is unique and should not be shared.

To export the CSR, **right-click on the key-pair we created and select Generate CSR**.

![csr settings](/images/tutorial-6/6-csr-settings.png "Default CSR settings.")

Keep the parameters as defaults and **save the CSR** in a place you'll remember.

## Step 3: Upload the CSR to APEX

### Log in to proxy gateway

![upload csr to apex](/images/tutorial-6/7-import-csr.png "Uploading CSR.")

Log into the proxy gateway. Go to the proxy APP we created in tutorial 5. We need to **upload the CSR** to this APP in order for APEX to generate the public certificate signed by APEX's root L2 certificate authority.

### Download signed public certificate

![export cred](/images/tutorial-6/8-export-pubcert.png "Export credentials to download.")

**Click on Export Credentials** to download the public certificate. Rename the downloaded certificate.cer file as **teamXX.cer**.

## Step 4: Import the signed public certificate

![import public cert](/images/tutorial-6/9-import-pubcert.png "Import public cert into Keystore.")

**Import the certificate file** into Keystore Explorer.

![cert chain](/images/tutorial-6/10-checkchain.png "Checking the cert chain.")

Once it's in, double check the certificate chain in the details. It should say **"teamXX"** under the L2 Root CA. Save the keystore file.

## Step 5: Export the private certificate

![export private cert](/images/tutorial-6/11-export-private.png "Export the private cert.")

We are now at the final step, exporting the private certificate. This is the file that will determine if you are able to access the API that has been secured with the L2 policy. In production, this file has to be kept secret and cannot be shared among different APPs.

Right-click the keystore and choose: **Export > Export Private Key**.

![OpenSSL](/images/tutorial-6/12-openssl.png "Choose OpenSSL.")

The format of the private key accepted by APEX is **.pem**. Chooose **OpenSSL** for this format.

![no encrypt](/images/tutorial-6/13-no-encrypt.png "No encryption.")

**Uncheck the encrypt checkbox** and click on **Export** to save the private key. Save this file someplace you remember. We will need to use this file again in tutorial 8 where we will do a "real world" test invoke of the bridging APIs.

We have finished with tutorial 6. Please move on to the next tutorial where we will change the policy of the proxy API to L2.
