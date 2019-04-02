# General Development and Coding Document

This guide outlines the best practice and coding conventions.

## Introduction

Here are some of the documents from where we derived our styling guide. If something isn't mentioned here, it's probably covered in great detail in one of these:

* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
* [Google Javascript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [Magento Programming Best Practices](https://devdocs.magento.com/guides/v2.3/ext-best-practices/extension-coding/common-programming-bp.html)
* [Magento Official Coding Standards](https://devdocs.magento.com/guides/v2.3/coding-standards/bk-coding-standards.html)
* [Knockout Js Introduction](https://knockoutjs.com/documentation/introduction.html)

## Version Control

- [Magento Cloud](https://accounts.magento.cloud/user)

  Do not mess up with `staging` branch, the `staging` branch will deploy to production. If the project is on live already, `staging` branch should always be ready for review.

- [Beanstalk](https://maginx.beanstalkapp.com/)

  If the project is on Beanstalk, then we have full control over the deployment process. Talk with *Edward* about which branch if you are not sure.
  
 - Maintainence Standard Workflow
 
  __The word 'master' here not necessaryly means `master` branch. It's the branch that deploy to live environment.__
  - Checkout master
  ```bash
  git checkout master
  ```
  - Make sure master is up to date
  ```bash
  git pull origin master
  ```
  - Checkout feature branch (Do NOT use a meaningless branch name)
  ```bash
  // you are on master
  git checkout -b feature-branch
  ```
  - Start your coding
  - After you are good with your code, commit the code on feature branch
  ```bash
  git add [<pathspec>…]
  git commit -m "git comment here"
  ```
  - Checkout qa or staging branch, whichever branch is used for client to review the updates
  ```bash
  git checkout qa
  // or
  git checkout staging
  ```
  - Merge the feature branch **into** test branch
  ```bash
  git merge feature-branch
  ```
  - Push your code to qa or staging branch, check your updates on staging environment
  ```bash
  git pull origin qa
  git push origin qa
  ```
  - Wait for approval from client or *Edward*
  - Once you are allowed to put your updated on live, checkout master
  ```bash
  git checkout master
  ```
  - Merge the feature branch **into** master
  ```bash
  git merge feature-branch
  // solve potential conflict here
  ```
  - Push master, check you updates on live environment
  ```bash
  git pull origin master
  git push origin master
  ```
