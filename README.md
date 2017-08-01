# Tutorial: Instructions for Creating a small Openshift API  catalog in 3scale. 

## Introduction
This tutorial draws on two 3scale Repos: 
1) [3scale CLI](https://github.com/3scale/3scale-cli)  
2) [API discovery](https://github.com/3scale/3scale-discover-APIs)    
For now this is non core functionality to 3scale but shortly we will be significantly enhancing our support for this area in the product. 
We will be constantly evolving this tutorial but for now we will import 4 OAI (Swagger) specs into 3scale - each of which will form an element of our catalog.  

## Steps
##### 1 - Get your 3scale domain and access token.
##### 2 - Import 4 OAI specs into 3scale.
##### 3 - Add our catalog files to our 3scale Developer Portal.
##### 4 - Modify our catalog files to reflect our API specs.
##### 5 - Test our catalog.  

## Prerequisites
Access to a 3scale Account - either SaaS or On Prem  

## 1 - Get your 3scale domain and access token.
First, get your 3scale domain.  
With SaaS it's the portion of your Admin URL between *http://* and *-admin.3scale.net*. e.g. with *https://plugin-admin.3scale.net* it's *plugin*  
With On Prem, it's the portion of your Admin URL between *http://* and the dot preceding the start of your host or IP. e.g. with *https://3scale-admin.amp.52.15.150.46.nip.io* it's *3scale-admin.amp*. We'll refer to this as your *3scale-domain*.  
Next, get your 3scale Access token (used to initialize the CLI). Go to Gear sign - Personal Settings - Tokens  
![01-threescale-accesstoken-1](https://raw.githubusercontent.com/tnscorcoran/3scale-api-catalog-setup/master/_images/01-threescale-accesstoken-1.png)
Add Access token  
![02-threescale-accesstoken-2](https://raw.githubusercontent.com/tnscorcoran/3scale-api-catalog-setup/master/_images/02-threescale-accesstoken-2.png)
Name it, give it read/write access to all scopes and Create Access token. Copy it (you won't be able to see it again).  
We'll refer to this your *3scale-access-token*   
![03-threescale-accesstoken-3](https://raw.githubusercontent.com/tnscorcoran/3scale-api-catalog-setup/master/_images/03-threescale-accesstoken-3.png)
  
  
## 2 - Import 4 OAI specs into 3scale.
*git clone* this repo
Go to the [3scale CLI](https://github.com/3scale/3scale-cli) for full instructions. Run the following:  
npm install -g node-3scale-cli  
3scale-cli config  
? 3scale access token: (enter your *3scale-access-token*)   
? 3scale id:  (enter your *3scale-domain*)   
? 3scale wildcard domain : (3scale.net or the rest of your 3scalehost)  
  
In your terminal, cd to where you cloned this repo. Run the following commands to import the OAI specs as Active Docs (Interactive Documentation) into 3scale. Each one will take couple of minutes :
3scale-cli activedocs create -f ./oai-spec-1-core-v1.json  
3scale-cli activedocs create -f ./oai-spec-2-openshiftIo_v1.json  
3scale-cli activedocs create -f ./oai-spec-3-autoscaling_v1.json  
3scale-cli activedocs create -f ./oai-spec-4-oauth-api.json  
# These fail on IMPORT - I have just manually entered them with these names (identical system names)
core-v1  
appsOpenshiftIo_v1  
autoscaling_v1  
oapi  
This is a good OAI spec validator: http://bigstickcarpet.com/swagger-parser/www/index.html



