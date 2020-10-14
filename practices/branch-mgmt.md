# Git Branch Naming Convention

Please follow these guidelines when working with Git on new features or bug fixes. 

#### New feature branches:

Each new feature should reside in its own branch. A feature branch uses `dev` as its parent branch. When a feature is complete, create a Pull Request \(PR\) back to `dev`. The PR will be squashed and merged after code review/testing of the feature.  
  
Naming convention: `feature/email_handler/feature_title`  
Example: `feature/vadim/gcp_billing_reports`

{% hint style="info" %}
Your email handler is the part of your email before the `@doit-intl.com`. 
{% endhint %}

**Hotfix branches:**

Hotfix branches are used to quickly patch issues/bugs with the production release. Hotfix branches use `master` as their parent branch. As soon as the fix is complete, the hotfix branch should be merged back to `master` and `dev` using a PR.

Naming convention: `hotfix/email_handle/issue_description`  
Example: `hotfix/vadim/support_page_crash`



