# Development and Coding Guidance

This guide outlines the best practice and coding conventions.

## Table of Contents

  1. [Introduction](#introduction)
  1. [Version Control](#version-control)
  1. [Coding](#coding)
  1. [Appendix](#author)

## Introduction

Here are some of the documents from where we derived our styling guide. If something isn't mentioned here, it's probably covered in great detail in one of these:

* [Magento Programming Best Practices](https://devdocs.magento.com/guides/v2.3/ext-best-practices/extension-coding/common-programming-bp.html)
* [Magento Official Coding Standards](https://devdocs.magento.com/guides/v2.3/coding-standards/bk-coding-standards.html)
* [Magento Technical Guidelines](https://devdocs.magento.com/guides/v2.3/coding-standards/technical-guidelines.html)

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
    - *Think twice before you remove any code in conflict*. If not sure, ask someone.
    - After you solve the conflict (remove all the `<<<<<<<` and `=======`), git `add` and  `commit` your change to finish the merge process.

------------
**[⬆ back to top](#table-of-contents)**

 ## Coding

 ~~Personally, I strongly recommend against using W3School~~
 
 Good coding materials:
  - [MDN web docs](https://developer.mozilla.org/en-US/)
  - [CSS tricks](https://css-tricks.com/)
  - [ECMAScript specification](https://tc39.es/ecma262/)
  - [Zend framework](https://framework.zend.com/manual/2.4/en/index.html)

### General coding style guide

###### Character Encoding
MUST use only UTF-8 without BOM [?](https://www.unicode.org/faq/utf_bom.html#BOM)

###### Line length
Each line is limited to be less than 120 characters

###### Indentations
- Tab size: 4 spaces
- Indent size: 4 spaces
- Continuation indent: 4 spaces

```html
<ul>
    <li>One</li>
    <li>Two</li>
</ul>
```

###### End of file
Add a blank line at the end of  file [:interrobang:](https://thoughtbot.com/blog/no-newline-at-end-of-file)

###### Spaces
Add space after keyword  `if` `for` `foreach` `switch`
Add spaced before and after equal operator `==` and assign operator `=` (except html)

```
Good
if (name == "Skywalker")

Bad
if(name=="Skywalker")
```
In a `for` statement, use no space before sem-color`;`,  add one space after semi-colon
Add spaces before and after comparison operator, llike `<` `>` `<=` `>=`
```
Good
for (i = 0; i < count; i++)
Bad
for(i=0;i<count;i++)
```
Add a space after colon `:`, and no space before colon
```
Good
<span data-bind="i18n: 'Update'"></span>
Bad
<span data-bind="i18n : 'Update'"></span>
<span data-bind="i18n:'Update'"></span>

```
Add a space right before open bracket `{`, except PHP
PHP requires class and function open bracket in a new line
```
Good
if (condition) {
} else if (otherCondition) {
} else {
}
Bad
if (condition){
} else if (otherCondition){
} else{
}
```
In the argument list, there MUST NOT be a space before each comma, and there MUST be one space after each comma.
```
Good
public function foo($arg1, &$arg2, $arg3 = [])
Bad
public function foo($arg1,&$arg2,$arg3 = [])
```


 ### HTML
 * [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML)
 * [W3C markup validation service](https://validator.w3.org/)
 * [Web Accessibility](https://www.w3.org/WAI/tips/developing/#top)


#### Tools
[HTML Symbols, Entities](https://www.toptal.com/designers/htmlarrows/)

#### Coding convention
   Magento provides HTML [style guide](https://devdocs.magento.com/guides/v2.3/coding-standards/code-standard-html.html)

### PHP
* [PHP_CodeSnifer](https://pear.php.net/manual/en/package.php.php-codesniffer.faq.php)
* [PHP standards (psr)](https://www.php-fig.org/psr/)

#### Coding convention
  PHP only, the open bracket for class and function MUST start on a new line
  ```PHP
  ###### Good
  <?php
  class ClassName
  {
      public function fooBarBaz($arg1, &$arg2, $arg3 = [])
      {
      // method body
      }
  }
  ###### Bad
  <?php
  class ClassName{
      public function fooBarBaz($arg1, &$arg2, $arg3 = []){
      // method body
      }
  }
  ```


### CSS


#### Tools
* [Color](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)
* [Squoosh](https://squoosh.app/)
* [Can I use?](https://caniuse.com/)
* [Targeting IE versions](https://codepen.io/mkstix6/pen/pRbErK)
* [CSS zen garden](http://csszengarden.com/)

#### Coding styles
* [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html)
* [Magento less coding standard](https://devdocs.magento.com/guides/v2.3/coding-standards/code-standard-less.html)

> ### Inline styling MUST be avoided ~~whatever the cost is~~

##### Braces
Add one space before opening braces and a line break after. Add a line break before closing braces.
###### Correct
```less
.nav {
    color: @nav__color;
}
```
###### Wrong
```less
.nav{color: @nav__color;}
```
##### Selector delimiters
Add a line break after each selector delimiter. Do not add spaces before or after delimiters.
###### Correct
```less
.nav,
.bar {
    color: @color__base;
}
```
###### Wrong
```less
.nav, .bar {
    color: @color__base;
}
```
##### !important property
Avoid using the !important property if possible. If it is required, add a space before the property.
###### Correct
```less
.jquery-ui-calendar-item {
    background-color: @nav__background-color !important;
}
```

#### Email styling
* [Email Template List in Magento 2](https://www.mageplaza.com/kb/email-template-list-magento-2.html)
* [The ultimate guide](https://www.campaignmonitor.com/css/selectors/universal/)

### JavaScript
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
* [Google Javascript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [Knockout Js Introduction](https://knockoutjs.com/documentation/introduction.html)
* [Magento Javascript coding standard](https://devdocs.magento.com/guides/v2.3/coding-standards/code-standard-javascript.html)

#### Tools
* [Babel](https://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=Q&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2%2Cenv&prettier=true&targets=&version=7.2.2)
* [Regex 101](https://regex101.com/)


**[⬆ back to top](#table-of-contents)**

## Author
- Daniel Qin daniel@maginx.com

## License
Copyright &copy; <2019> Daniel Qin

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
