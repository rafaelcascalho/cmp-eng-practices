---
description: >-
  We prefer to stick to the languages and frameworks we already use, support and
  maintain unless the there are strong reasons for adding a new language to our
  stack.
---

# Programming Languages

## Programming Languages

The current stack of programming languages for the CMP is:

* Go 11+
* Python 3.0+
* NodeJS 10+

The majority of the CMP codebase is written in **golang**. We like golang because it's easy to learn, have good support for concurrency and good quality client libraries for Google Cloud and Amazon Web Services. It also runs on Google App Engine, platform we use to run the CMP.

**Python** is mostly used when we need the support for frameworks such as [pandas](https://pandas.pydata.org/) or [pmdarima](https://alkaline-ml.com/pmdarima/index.html) or when there is no client library available for golang. For example, we use [Algolia](https://www.algolia.com/) for free text search and there is no golang client library \(as of late 2020\).

Finally, **NodeJS** is the less used language. It's our final fallback for use cases when we need Javascript support to interact with DOM \(e.g. scrapers\). 

