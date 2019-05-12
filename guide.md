(setq markdown-xhtml-header-content
      "<style type='text/css'>
a { text-decoration: none; }
a:hover { text-decoration: underline; }
</style>")
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
    1. Checkout master
    ```bash
    git checkout master
    ```
    2. Make sure master is up to date
    ```bash
    git pull origin master
    ```
    3. Checkout feature branch (Do NOT use a meaningless branch name)
    ```bash
    // you are on master
    git checkout -b feature-branch
    ```
    4. Start your coding
    5. After you are good with your code, commit the code on feature branch
    ```bash
    git add [<pathspec>…]
    git commit -m "git comment here"
    ```
    6. Checkout qa or staging branch, whichever branch is used for client to review the updates
    ```bash
    git checkout qa
    // or
    git checkout staging
    ```
    7. Merge the feature branch **into** test branch
    ```bash
    git merge feature-branch
    ```
    8. Push your code to qa or staging branch, check your updates on staging environment
    ```bash
    git pull origin qa
    git push origin qa
    ```
    9. Wait for approval from client or *Edward*
    10. Once you are allowed to put your updated on live, checkout master
    ```bash
    git checkout master
    ```
    11. Merge the feature branch **into** master
    ```bash
    git merge feature-branch
    // solve potential conflict here
    ```
    12. Push master, check you updates on live environment
    ```bash
    git pull origin master
    git push origin master
    ```

___

- Solve git conflict

    ___It's crucial you solve the conflict in the approriapte manner. If done in the wrong way, you might remove code of someone else.___

    - Example of conflict
    ```
    $ git merge new_branch_to_merge_later
    Auto-merging merge.txt
    CONFLICT (content): Merge conflict in merge.txt
    Automatic merge failed; fix conflicts and then commit the result.
    ```

    - What a conflict looks like    
    ```
    $ cat merge.txt
    <<<<<<< HEAD
    this is some content to mess with
    content to append
    =======
    totally different content to merge later
    >>>>>>> new_branch_to_merge_later
    ```
    
    + If the conflict code contains your updates, you might want to keep the part between `<<<<<<< HEAD` and `=======`
    + If the conflict code is not related to your updates, you might want to keep the part between `=======` and `>>>>>>> new_branch_to_merge_later`
    - Think twice before you remove any code in conflict. If not sure, ask someone.
    - After you solve the conflict (remove all the `<<<<<<<` and `=======`), commit your change to finish the merge process.
    
    
 ## Coding
 
 ~~Personally, I strongly recommend against using W3School~~
 
 ### HTML
 
   For reference, [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML)
   - Coding convention, 
