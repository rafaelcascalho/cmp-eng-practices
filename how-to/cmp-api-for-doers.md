---
description: How to generate your API key and integrate with the CMP
---

# CMP API for Do'ers!

### **Creating a token**

In order to allow DoiT employees to create a token, follow the procedure below.

Using this token, the Doit employee can run [DoiT APIs](https://developer.doit-intl.com/) with a specific customer context.

1. **Get your firebase token:**
   1. Login to CMP 
   2. Open the DevTools \(right click + inspect\)
   3. In the Network Tab, search for “api/” and copy the Token

![](https://lh5.googleusercontent.com/25enmfoRJFMqhdD7NfV7B7t2C3qEbfETa2cmcykNXeAnX7ev8AD8cwokQ2Kk1Og7nsuI1zW3HSObjVVKsz7OKvCDz-aqH2K5tNTGs1RTtgo0CDrJf1iQg9TKyB8Fqh59iKM6rri3)

2. Use HTTP client \(curl, Postman…\) to create the token.

 Replace the XXXXXX with the token you got in step 1.

  **`curl --location --request POST '`**[**`http://hello.doit-intl.com/api/v1/users/generateApiToken`**](http://hello.doit-intl.com/api/v1/users/generateApiToken)**`' \`**

**`--header 'Content-Type: application/json' \`**

**`--header 'Authorization: Bearer XXXXXX' '`**

The response you’ll get: 

![](https://lh3.googleusercontent.com/ykdkYwNic5_dLEriQgSIXur3DUKUxaASt0q6gRO7dSKwHSwk-v-XLVivEG4soJOzWlZYkH0YH8dxXQA1zc4v0bKw_tcoEF3py9B1k2frOcFi8M8jizpYa4CqOASbqn3lrCgcmEkN)

### **Using the Token**

The Token can be used with any of the APIs described in the [CMP API developer Hub](https://developer.doit-intl.com/).

In order to set the customer context and run an API, you should add the “**customerContext**” param to the request.

The value of the “customerContext” param should be the customer-id.

For example in order to get the invoices of “budgetao.io” customer, use the following CURL command:  
****

**`curl --location --request GET 'https://api.doit-intl.com/billing/v1/invoices/?customerContext=g1oluuJ7Jw0Qna4FBEl0' \`**

**`--header 'Content-Type: application/json' \`**

**`--header 'Authorization: Bearer XXXXXX' \`**

The 'XXXXXX' should be replaced with the Token you got in step 2.  


