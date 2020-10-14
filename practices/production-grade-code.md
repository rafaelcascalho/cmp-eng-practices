---
description: >-
  When releasing features/epics to production, the code itself is just a part of
  the job. This article discusses best practices for building production-grade
  capabilities under the scope of CMP.
---

# Writing Production-Grade Code

You've just finished debugging your code and everything looks great. You feel good and already anticipate the excitement of the deployment to the production and first customers starting to enjoy your new feature. We all know this feeling.

Before you commit your code, please pause and make sure you've not forgotten to think \(and implement!\) what would make the difference between just a code and the production-grade code. 

### **Use the right Repository**

In most cases, your code should reside in the [https://github.com/doitintl/hello-cmp](https://github.com/doitintl/hello-cmp) repository. using a pull request so the Cloud Build could read it during the deployment process. Our main deployment automation based on Google Cloud Build will only pull code from this repository for security purposes.

If you can make a strong case for your feature \(security concerns, unique configuration, etc.\), your code can be hosted in a separate repository. The name of this repository have to start with `cmp-` \(see examples such as `cmp-forecasting` or `cmp-zendesk-app`.

### **Deployment**

You need to have a clear understanding of how your code is going to be deployed initially, and every next time when your pull requests are approved. For example, each time you add Cloud Function or Cloud Run to the project, they need to be specifically deployed. Check [cloudbuild.json](https://github.com/doitintl/hello-cmp/blob/master/configuration/cloudbuild.prod.json) for more details.

### **Environment**

Your code should be aware of the environment it's running in and act accordingly. There is a difference if your code runs locally on your laptop, the dev/staging environments, or in the production environment. Where applicable, use this simple case:

{% tabs %}
{% tab title="Go" %}
```go
if common.Production {
     // Running on GAE, on the production project
} else if !IsLocalhost {
     // Running on GAE, but not in the production project
     // This may be the dev project or your playground
} else {
     // Running locally...
}

```
{% endtab %}

{% tab title="Client" %}
```javascript
if (process.env.NODE_ENV === "production") {
    console.log("Running the production build");
}
```
{% endtab %}
{% endtabs %}

### **Secrets**

Never store secrets in the repository or locally on your laptop. All secrets should be stored in the Google Secret Manager \(GSM\) and consumed from there when you need them. Secrets are only to be used in the backend; under no circumstances should you include a secret file in the client's code.  
  
Use our `secretmanager` package to access secrets stored in GSM from the backend:

{% tabs %}
{% tab title="Go" %}
```go
// Define the secret structure, secrets are usually created in JSON format
type secret struct {
	BaseURL string `json:"base_url"`
	APIKey  string `json:"api_key"`
}

// Retrieve the latest version for "MySecret" secret
secretPayload, err := secretmanager.AccessSecretLatestVersion(ctx, secretmanager.MySecret)
if err != nil {
	// handle error
}

// Unmarshal the secret payload to a usable variable
var mySecret secret
if err = json.Unmarshal(secretPayload, &mySecret); err != nil {
	// handle error
}

```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
If you require a new secret that is currently not available in GSM, please discuss this with your Staff Software Engineer \(SSE\).
{% endhint %}

### **Observability**

Observability ****helps our product, customer success, and engineering teams to understand how CMP is being adopted by our customers and users. 

It can be achieved by sending events to [Mixpanel](https://mixpanel.com/), the tool we use to collect user events. Your code should emit events for all major actions of the feature, preferably with event properties for additional context.

{% hint style="info" %}
Events should follow naming convention - `feature[.sub-feature].action-name[.sub-action]`.  
For example, `analytics.reports.new` is the event when a new Cloud Analytics report is created. 
{% endhint %}

Check the reference events implementation for more details:

{% tabs %}
{% tab title="Client" %}
```javascript
import mixpanel from "../../utils/mixpanel";

// mixpanel.track(event_name, event_properties)
mixpanel.track("analytics.reports.new", { 
    reportId: docRef.id, 
    draft: isDraft 
});
```
{% endtab %}

{% tab title="Go" %}
```text
// WIP
```
{% endtab %}
{% endtabs %}

### **Logging**

Your code should handle errors gracefully and log the errors accordingly. Always send your logs to Google Cloud Logging using this .... function so these errors could be aggregated, analyzed, and correlated with other errors when we try to troubleshoot the outage or a bug.  

```text
TODO: Code example
```

### **Monitoring**

How do you know your feature is working? How others can know it is working too? Your code should implement a logic that Google Monitoring \(aka Stackdriver\) can use to generate alerts when something is wrong.

For monotonously running tasks \(aka scheduled tasks\), a common practice is to emit custom metrics each time the task is running successfully. Then, with Google Monitoring, configure an alert based on metric absence for longer than two subsequent runs. For example, if your task is running every hour, configure the alert to trigger after two hours of the absent metric.

{% hint style="info" %}
Custom metrics should follow naming convention - `cmp.feature-name.task-name`. For example, `cmp.analytics.etl.refresh` is the metric added each time the ETL refreshes the analytics data. 
{% endhint %}

Check the reference custom metric implementation for more details:

```text
TODO: Code example
```

### **Operational Playbook**

As a software engineer, you know the most nitty-gritty details of your implementation. Try to document as much as possible in the operational playbook so others could operate this feature when you're not available.  

Check our [internal docs](https://app.gitbook.com/@doitintl/s/cmp-ops/operational-playbooks/forecasting-time-series) for examples, and don't forget to add yours!

