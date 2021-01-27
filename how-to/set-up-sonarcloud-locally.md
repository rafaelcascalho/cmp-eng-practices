---
description: >-
  Step by step guide -> Integrate SonarCloud service to your local IDE using
  SonarLint extension/plugin
---

# Set up SonarCloud locally



Follow steps related to your IDE. Instructions regarding credentials generation can be found at the bottom along with contacts to reach in case of configurations issues.

{% tabs %}
{% tab title="VSCode IDE" %}
1. [ ] **Install `SonarLint` extension \(EXTENSIONS MARKETPLACE tab on the left side\)**
2. [ ] **Find your settings.json file:**

Using URL Directory:

*  `~/Library/ApplicationSupport/Code/User/`**`settings.json`**

Or

* `/Users/{`_`YOUR_USER`_`}/Library/ApplicationSupport/Code/User/`**`settings.json`**

Using IDE menu:

* _Code -&gt; Preferences  -&gt; Settings_ \(or simply click **CMD** + **,** \)
* Under _User_  tab choose _Extensions -&gt; SonarLint_
* Click _“Edit in settings.json”_

\_\_

* [ ] **Insert the properties below in your settings.json file:**

```javascript
    "sonarlint.connectedMode.project": {
        "projectKey": “YOUR_PROJECT_KEY”
    },
    "sonarlint.connectedMode.connections.sonarcloud": [
        {
            "connectionId": "doitintl_sonarcloud",
            "organizationKey": "doitintl",
            "token": “YOUR_PRIVATE_TOKEN”
        }
    ],
    "sonarlint.output.showAnalyzerLogs": true,
    "sonarlint.output.showVerboseLogs": true
```

{% hint style="info" %}
See how to generate your credentials below
{% endhint %}



### Use:

* Issues will be prompted as an integrated part of your IDE 
* PROBLEMS tab -&gt; shows aggregated issues for all of your currently open files \(vscode tabs\)
* OUTPUT tab - \(choose SonarLint on the right side dropdown\) -&gt;  prints any action taken by the extension package \(log\)
{% endtab %}

{% tab title="JetBrains/IntelliJ IDE\'s" %}
1. [ ] **Install `SonarLint` plugin:**

_IDE\_NAME -&gt; Preferences_ \(or simply click **CMD** + **,** \) _-&gt; plugins_  and search under Marketplace tab

1. [ ] **Restart your IDE**
2. [ ] **Configure SonarCloud connection to SonarLint:**

_Preferences -&gt; Tools -&gt; SonatLint \(_general settings - not project settings\)

1. [ ] **Under** _SonarQube/SonarCloud_ _connections_ **click** **+**
2. [ ] **Choose** S_onarCloud_ **, set a** _Connection Name_ **\(“doitintl\_sonarcloud” for instance\) and click next**
3. [ ] **Insert `YOUR_PRIVATE_TOKEN` and click next**
4. [ ] **Under** _your organization_ **choose `DoiT International (doitintl)` and click next until the window is closed**
5. [ ] **Go to SonarLint/Project settings:**

_Preferences -&gt; Tools -&gt; SonatLint -&gt; Project settings -&gt; Bind to SonarQube/SonarCloud_  tab

1. [ ] **Make sure** _Bind project to SonarQube/SonarCloud_  **is selected**
2. [ ] **Under** _Connection_  **choose your recently created connection name \("doitintl\_sonarcloud" etc..\)**
3. [ ] **Under** _Project_  **set `YOUR_PROJECT_KEY`**

{% hint style="info" %}
See how to generate your credentials below
{% endhint %}

### 

### Use:

* Issues will be prompted as an integrated part of your IDE 
* On SonarLint tab:

  * Current file -  shows issues related to the current file
  * Log - prints any action taken by the plugin package
{% endtab %}
{% endtabs %}



## Credentials

#### **Get your private Token** 

1. Make sure you are signed in to [https://sonarcloud.io/](https://sonarcloud.io/) with your _GitHub_ account
2. Go to [security section on your account](https://sonarcloud.io/account/security/) and generate a private token \(token name is meaningless\) 



#### Find your Project Key

Most likely your project key will be structured in that form: _`doitintl_PROJECTNAME`_

For example `doitintl_bd` or `doitintl_hello-cmp` or `doitintl_cmp-cost-anomalies` etc..

It can be found using [DoiT International's projects list](https://sonarcloud.io/organizations/doitintl/projects) :

Choose **your main project** and then:

* You will see the `Project Key` on the bottom right side

OR 

* As the `id` property of the url \(example - [https://sonarcloud.io/dashboard?id=_**doitintl\_hello-cmp**_](https://sonarcloud.io/dashboard?id=doitintl_hello-cmp) _**\)**_

_\*\*\*\*_

{% hint style="warning" %}
If you are having configuration issues feel free to contact [ofir.cohen@doit-intl.com](mailto:ofir.cohen@doit-intl.com)
{% endhint %}

{% hint style="warning" %}
If you are having permissions issue or cannot sign in to SonarCloud please contact [dror@doit-intl.com](mailto:dror@doit-intl.com)
{% endhint %}

