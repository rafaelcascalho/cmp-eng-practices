# Git Workflow and Conventions

Please follow these guidelines when working with Git on new features or bug fixes for CMP. 

### Commit Messages

Always add a meaningful commit message describing the changes you have made.

{% hint style="success" %}
**DO:**  
&lt;commit message&gt;:   
Fix Flex RI order dialog region and pricing issue  
&lt;new line&gt;  
&lt;commit description&gt;:  
- Remove regions that are not supported by Flex RI from the customer order dialog  
- Present an error alert when selecting an unsupported instance type
{% endhint %}

{% hint style="danger" %}
**DON'T:**  
Write commit messages such as the following: ".", "wip", "new feature", "fix", "bug" etc.
{% endhint %}

### Branch Naming Conventions

#### New feature branches

Each new feature should reside in its own branch. A feature branch uses `dev` as its parent branch. When a feature is complete, create a Pull Request \(PR\) back to `dev`. The PR will be squashed and merged after code review/testing of the feature.  
  
Naming convention: `feature/email_handler/my_feature_title`  
Example: `feature/vadim/gcp_billing_reports`

{% hint style="info" %}
Your email handler is the part of your email before the `@doit-intl.com`
{% endhint %}

{% hint style="info" %}
Use `snake_case` in your branch names
{% endhint %}

**Hotfix branches**

Hotfix branches are used to quickly patch issues/bugs with the production release. Hotfix branches use `master` as their parent branch. As soon as the fix is complete, the hotfix branch should be merged back to `master` and `dev` using a PR.

Naming convention: `hotfix/email_handle/my_issue_description`  
Example: `hotfix/vadim/support_page_crash`



