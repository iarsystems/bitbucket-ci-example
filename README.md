<img align="right" src="https://github.com/user-attachments/assets/c3870204-20be-4281-9fa7-016a4999734b" width="96px" />


# IAR Build Tools for Arm on Bitbucket Pipelines


>[!WARNING]
>The information in this repository is subject to change without notice and does not constitute a commitment by IAR. While it serves as reference model for implementing Continuous Integration with IAR Tools, IAR assumes no responsibility for any errors, omissions, or specific implementations.


## Introduction
This repository provides a reasonably simple example to start with, alongside general guidelines on how a CI/CD pipeline can be set up on [Bitbucket](https://bitbucket.org), using [Bitbucket-hosted runners]() to automatically build, test, and deploy a project with the [IAR Build Tools for Arm](https://www.iar.com/embedded-development-tools/embedded-ci-cd).

In case you need an introduction on how to get started with Bitbucket, refer to [Getting started with Bitbucket](https://bitbucket.org/product/guides).


## Prerequisites
Before you begin, you will need:
- A CI Token for the IAR Build Tools[^1]
- A [Bitbucket account][url-bb-join].


## Quickstart
### Importing the repository
Under your Bitbucket account:
- Click `  Import repository  `. (`https://bitbucket.org/<username>/workspace/repository/import`)
- Fill **Old repository** with this repository's URL.
- Set the __Project name*__. (e.g., `ci`)
- Set the __Repository name*__. (e.g., `bitbucket-ci-example`)
- Set the __Access level__ to [x] Private.
- Finally click **Import repository**.
Once the importing process is complete, Bitbucket will take you to your newly imported repository.

### Setting up your CI Token
Under your __Repository settings__:
- Enter a new _secret_ repository variable uner __Repository variables__.
- Name it `IAR_LMS_BEARER_TOKEN`, and paste your CI Token under __Value__.
![image](https://github.com/user-attachments/assets/a2c8fbab-05d6-4505-aa72-b7812fcc3c59)
- Make sure __Secured__ is selected and click `  Add  `.
![image](https://github.com/user-attachments/assets/567523ce-e3ef-4452-8e86-5441a04d336a)


## Bitbucket pipeline example
On your private repository, navigate to [bitbucket-pipelines.yml](bitbucket-pipelines.yml) workflow file. This file uses the [Bitbucket-flavored YAML][url-bb-doc-pipeline] to describe an example of a pipeline workflow containing multiple jobs typically performed in embedded firmware projects.

>[!NOTE]
>- Refer to the [bitbucket-pipelines.yml](bitbucket-pipelines.yml) workflow file for detailed comments.
>- Learn how to [configure your pipeline][url-bb-doc-pipeline].

### Test your pipeline
Now we are good to perform a quick test to see if your runner is taking jobs properly.
- From the repository page, go to __Settings__ → __Pipelines__.
- Check [x] __Enable Pipelines__.
- Go to __Pipelines__ → __Run pipeline__.

![image](https://github.com/user-attachments/assets/93bc780b-aee2-4682-a529-0d4d8c5b20fb)

Now you and/or your team can start pushing code to your repository and get automated results. 


## Summary
This example provided an overview of how to get started with the IAR Build Tools for Arm on Bitbucket pipelines. Development teams can immediately benefit from the comprehensive feedback these modern workflows offer, enabling them to quickly build, analyze, test, and deploy with high quality.

[__` Follow us `__][url-gh-iar] on GitHub to get updates about examples like this and more.


## Issues
For technical support contact [IAR Customer Support][url-iar-customer-support].

For questions or suggestions related to this example: try the [wiki][url-repo-wiki] or check [earlier issues][url-repo-issue-old]. If those don't help, create a [new issue][url-repo-issue-new] with detailed information.

[^1]: The use of the IAR Build Tools is subject to the [IAR Software License Agreement](https://github.com/iarsystems/bitbucket-ci-example/blob/master/LICENSE.md) and requires a valid subscription-based activation token for operation. If you are not yet a subscriber, please [contact us](https://iar.com/about/contact) for more information.

<!-- links -->
[url-iar-customer-support]: https://iar.my.site.com/mypages/s/contactsupport
[url-iar-bxarm]: https://www.iar.com/bxarm
[url-gh-iar]: https://github.com/iarsystems
    
[url-bb-doc-pipeline]: https://support.atlassian.com/bitbucket-cloud/docs/configure-your-pipeline/
[url-bb-doc-yaml]: https://support.atlassian.com/bitbucket-cloud/docs/configure-your-runner-in-bitbucket-pipelines-yml/
[url-bb-doc-runner]: https://support.atlassian.com/bitbucket-cloud/docs/runners
[url-bb-join]: http://www.atlassian.com/try/cloud/signup?bundle=bitbucket

[url-repo]: https://github.com/iarsystems/bitbucket-ci-example
[url-repo-wiki]: https://github.com/iarsystems/bitbucket-ci-example/wiki
[url-repo-issue-new]: https://github.com/iarsystems/bitbucket-ci-example/issues/new
[url-repo-issue-old]: https://github.com/iarsystems/bitbucket-ci-example/issues?q=is%3Aissue+is%3Aopen%7Cclosed
