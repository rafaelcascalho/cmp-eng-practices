**Abstract:**

This guide explains how to setup your own CMP playground using your own Google Cloud sandbox (e.g. `yourname-playground`)

1. Start by cloning hello-cmp project

2. Open the project in your favorite IDE we will use VS code in this guide

# Server-side config
Open the init file: hello-cmp/server/services/default/init.js
and change the default project to your project
![](https://raw.githubusercontent.com/doitintl/hello-cmp/master/images/server_config_cmp.png)

# Client-side config
1. Open client/.firebaserc file, under "projects" change set the default to your project.

![](https://raw.githubusercontent.com/doitintl/hello-cmp/master/images/client_fbrc_cmp.png)

2. Open the .env file it might be called .env.development if so rename it .env
    Go to Firebase console choose your project open settings page and copy your project details.
    
    Change the following values:
    * PROJECT_ID
    * SENDER_ID
    * REACT_APP_FIREBASE_API_KEY
    * REACT_APP_FIREBASE_APP_ID


```
PROJECT_ID="<lior-playground>"
SENDER_ID="<Cookies_delivery>"
REACT_APP_FIREBASE_API_KEY="<Cookies>"
REACT_APP_FIREBASE_MESSAGING_SENDER_ID="$SENDER_ID"
REACT_APP_FIREBASE_APP_ID="<x:$SENDER_ID:web:xxxx>"
REACT_APP_FIREBASE_AUTH_DOMAIN="$PROJECT_ID.firebaseapp.com"
REACT_APP_FIREBASE_DATABASE_URL="https://$PROJECT_ID.firebaseio.com"
REACT_APP_FIREBASE_PROJECT_ID="$PROJECT_ID"
REACT_APP_FIREBASE_STORAGE_BUCKET="$PROJECT_ID.appspot.com"
REACT_APP_MIXPANEL_TOKEN="<MixpnelDevToken>"
REACT_APP_STRIPE_PUBLISHABLE_KEY="<pk_test_xxx>"
GENERATE_SOURCEMAP=true
REACT_APP_LOGGER=true
REACT_APP_PLAID_ENV="sandbox"
REACT_APP_PLAID_PUBLIC_KEY="<PUBLIC_KEY>"
```    

# Secrets
You will need to add secrets files to your project at secret manager.<br/>
This is the current secrets list it may vary over time

![](https://raw.githubusercontent.com/doitintl/hello-cmp/master/images/secrets_list.png)