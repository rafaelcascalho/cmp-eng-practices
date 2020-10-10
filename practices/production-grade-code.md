---
description: >-
  When releasing features/epics to production, the code itself is just a part of
  the job. This article discusses best practices for building production-grade
  capabilities under the scope of CMP.
---

# Writing Production-Grade Code

You've just finished debugging your code and everything looks great. You feel good and already anticipate the excitement of the deployment to the production and first customers starting to enjoy your new feature. We all know this feeling.

Before you commit your code, please pause and make sure you've not forgotten to think \(and implement!\) what would make the difference between just a code and the production-grade code. 

**Use the right Repository**

In most cases, your code should be committed to [https://github.com/doitintl/hello-cmp](https://github.com/doitintl/hello-cmp) repository using a pull request so the Cloud Build could read it during the deployment process.  Our main deployment automation based on Google Cloud Build will only pull code from this repository for security purposes.

**Deployment**

You need to have a clear understanding about how your code is going to be deployed initially and every next time when your pull requests are approved. For example, each time you add Cloud Function or CloudRun to the project, they need to be specifically deployed. Check [cloudbuild.json](https://github.com/doitintl/hello-cmp/blob/master/configuration/cloudbuild.prod.json) for more details.

**Environment**

Your code should be aware of environment it's running in and act accordingly. There is a difference if your code runs locally on your laptop, the dev/staging environments or in the production environment. Where applicable, use this simple case:

```text
TODO: Code example
```

**Secrets**

Never store secrets in the repository or locally on your laptop. All secrets should be stored in the Google Secret Manager and consumed from there when you need them.

**Observability**

Observability ****helps our product, customer success and engineering teams to understand how CMP is being adopted by our customers and users. 

It can be achieved by sending events to [Mixpanel](https://mixpanel.com/), the tool we use to collect user events. Your code should emit events for all major actions of the feature, preferably with event properties for additional context.

{% hint style="info" %}
Events should follow naming convention - `cmp.feature-name.action-name`. For example, `cmp.analytics.reports.new` is the event when new Cloud Analytics report is created. 
{% endhint %}

Check the reference events emitment implementation for more details:

```text
TODO: Code example
```

**Monitoring**

How do you know your feature is working? How others can know it is working too? Your code should implement a logic which Google Monitoring \(aka Stackdriver\) can use to generate alerts when something is wrong.

For monotonously running tasks \(aka scheduled tasks\), a common practice is to emit custom metrics each time the task is running successfully. Then, with Google Monitoring, configure an alert based on metric absence for longer than two subsequent runs. For example, if your task is running every hour, configure the alert to trigger after two hours of absent metric.

{% hint style="info" %}
Custom metrics should follow naming convention - `cmp.feature-name.task-name`. For example, `cmp.analytics.etl.refresh` is the metric added each time the ETL refreshes the analytics data. 
{% endhint %}

Check the reference custom metric implementation implementation for more details:

```text
TODO: Code example
```

**Logs**

Your code should handle errors gracefully and log the errors accoaccordly. Always send your logs to Google Cloud Logging using this .... function so these errors could be aggregated, analyzed and correlated with other errors when we try to troubleshoot the outage or a bug.  

```text
TODO: Code example
```

**Operational Playbook**

As a software engineer, you know the most nitty gritty details of your implementation. Try to document as much as possible in the operational playbook so others could operate this feature when you're not available.  

Check the Operation Playbooks Wiki for examples \(and add yours!\)

