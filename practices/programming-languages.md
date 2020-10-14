---
description: >-
  We prefer to stick to the languages and frameworks we already use, support and
  maintain unless the there are strong reasons for adding a new language to our
  stack.
---

# Programming Languages

## Programming Languages

The current stack of programming languages for the CMP is:

| Running Environment | Language/Framework | Version |
| :--- | :--- | :--- |
| Google App Engine default service | Node.js | v12 |
| Google App Engine backend services | Go | v1.14 |
| Firebase functions \(Firestore triggers\), Google Cloud Functions | Node.js | v12 |
| CMP Browser Client | React | v16.13 |
| Other | Python | v3.8 |

The majority of the CMP backend codebase is written in **Go programming language**.  
We like to use Go because it's relatively easy to learn, has good support for concurrency, and has good quality client libraries for Google Cloud and Amazon Web Services. It is also supported by the Google App Engine standard \(2nd generation\) platform.

**Node.js** is mostly used for Firebase or Google cloud functions. The support for Go on these platforms is still limited.

Finally, **Python** is the less used language. It's our final fallback for use cases when we need the support for frameworks such as [pandas](https://pandas.pydata.org/) or [pmdarima](https://alkaline-ml.com/pmdarima/index.html) or when there is no client library available for Go.



