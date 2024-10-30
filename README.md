<img align="right" src="https://github.com/user-attachments/assets/c3870204-20be-4281-9fa7-016a4999734b" width="96px" />


# IAR Build Tools for Arm on Bitbucket using Linux runners


>[!WARNING]
>The information in this repository is subject to change without notice and does not constitute a commitment by IAR. While it serves as a valuable reference for DevOps Engineers implementing Continuous Integration with IAR Tools, IAR assumes no responsibility for any errors, omissions, or specific implementations.


## Introduction
From a CI/CD perspective, the [IAR Build Tools for Arm](https://iar.com/bxarm) comes with everything you need to build embedded firmware projects from the command line. This tutorial provides a simple example with general guidelines on how to set up a CI/CD pipeline using [Bitbucket](https://bitbucket.org/) while taking advantage of the so-called [Bitbucket self-hosted runners][url-bb-doc-runner].

In case you need an introduction on how to get started with Bitbucket, refer to [Getting started with Bitbucket](https://bitbucket.org/product/guides).


## Prerequisites
Before you begin, you will need to download and install the following:
- IAR Build Tools for Arm 9.60.2 for Ubuntu 22.04 x64 ([`bxarm-9.60.2.deb`](https://updates.iar.com/?product=BXARM&version=9.60))
   - IAR customers can download it directly from [IAR MyPages](https://iar.my.site.com/mypages). If you do not have a license, [contact IAR Sales](https://iar.com/about/contact).

You also will need
- A [Bitbucket account][url-bb-join].


## Quickstart
Under your Bitbucket account:
- Click `  Import repository  `. (`https://bitbucket.org/<username>/workspace/repository/import`)
- Fill **Old repository** with this repository's URL.
- Set the __Project name*__. (e.g., `ci`)
- Set the __Repository name*__. (e.g., `bx-bitbucket-ci`)
- Set the __Access level__ to [x] Private.
- Finally click **Import repository**.

Once the importing process is complete, Bitbucket will take you to your newly imported repository.


## Bitbucket pipeline example
On your private repository, navigate to [bitbucket-pipelines.yml](bitbucket-pipelines.yml) workflow file. This file uses the [Bitbucket-flavored YAML][url-bb-doc-pipeline] to describe an example of a pipeline workflow containing multiple jobs typically performed in embedded firmware projects.

>[!NOTE]
>- Refer to the [bitbucket-pipelines.yml](bitbucket-pipelines.yml) workflow file for detailed comments.
>- Learn how to [configure your pipeline][url-bb-doc-pipeline].


## Adding runners to your repository
Bitbucket makes it easy to setup a new self-hosted runner in a Linux host. Add a self-hosted runner to your build to run pipelines on your own Linux server with the IAR Build Tools for Arm pre-installed:
- Go to __Repository settings__ → __Pipelines__ → __Runners__ → __Add runner__.
- Click `  Add runner  `.
- Select __`Linux shell`__ as __System and architecture*__.
- Set your runner's name in __Runner name*__ (e.g., `bxarm-runner`).
- Leave __Runner labels*__ on its default (`self.hosted`, `linux.shell`).
- Click `  Next  `.

>[!TIP]
>A "Runner installation" frame will pop-up containing your exclusive steps for __a)__ downloading the runner archive, **b)** extracting the archive, and finally **c)** launching the runner. Each of these steps provide you with a "Copy command" button, located at the right-side of each step.

- Once you have the Bitbucket runner software installed and running on your server, click `   Next   `.

>[!TIP]
>The last wizard's screen provides hints for using the Bitbucket Runner you just added in a pipeline workflow file.
>
>![image](https://github.com/user-attachments/assets/4517c887-6ebd-4f2c-95c8-561e418fd8d8)

- Click `  Finish  ` and you will be taken back to the page where you can see your active runners as well as add more runners.

You can have as many parallel build nodes with runners as your license allows you to. [Contact IAR Sales](https://iar.com/about/contact) for expanding your build capacity.

### Test your runner
Now we are good to perform a quick test to see if your runner is taking jobs properly.
- From the repository page, go to __Settings__ → __Pipelines__.
- Check [x] __Enable Pipelines__.
- Go to __Pipelines__ → __Run pipeline__.

![image](https://github.com/user-attachments/assets/bb0678ec-2617-4e6f-a98e-558c45cfcd19)

Now you and/or your team can start pushing code to your repository and get automated results. 


## Summary
This tutorial provided an overview of how to get started with the IAR Build Tools for Arm on Bitbucket pipelines using self-hosted Linux runners. Development teams can immediately benefit from the comprehensive feedback these modern workflows offer, enabling them to quickly build, analyze, test, and deploy with high quality.

[__` Follow us `__][url-gh-iar] on GitHub to get updates about tutorials like this and more.


## Issues
For technical support contact [IAR Customer Support][url-iar-customer-support].

For questions or suggestions related to this tutorial: try the [wiki][url-repo-wiki] or check [earlier issues][url-repo-issue-old]. If those don't help, create a [new issue][url-repo-issue-new] with detailed information.


<!-- links -->
[url-iar-customer-support]: https://iar.my.site.com/mypages/s/contactsupport
[url-iar-bxarm]: https://www.iar.com/bxarm
[url-gh-iar]: https://github.com/IARSystems
    
[url-bb-doc-pipeline]: https://support.atlassian.com/bitbucket-cloud/docs/configure-your-pipeline/
[url-bb-doc-yaml]: https://support.atlassian.com/bitbucket-cloud/docs/configure-your-runner-in-bitbucket-pipelines-yml/
[url-bb-doc-runner]: https://support.atlassian.com/bitbucket-cloud/docs/runners
[url-bb-join]: http://www.atlassian.com/try/cloud/signup?bundle=bitbucket

[url-repo]: https://github.com/IARSystems/bx-bitbucket-ci
[url-repo-wiki]: https://github.com/IARSystems/bx-bitbucket-ci/wiki
[url-repo-issue-new]: https://github.com/IARSystems/bx-bitbucket-ci/issues/new
[url-repo-issue-old]: https://github.com/IARSystems/bx-bitbucket-ci/issues?q=is%3Aissue+is%3Aopen%7Cclosed
