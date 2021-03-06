# Rowley Visual Configurator Development Guide

*A particular introduction of Rowley Visual Configurator*

> **Note**: this guide assumes you are familiar with Magento 2 MVC and [module file structure](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/build/module-file-structure.html). It also assumes you understand Magento 2 [product types](https://docs.magento.com/m2/ee/user_guide/catalog/product-types.html) and cart/checkout process.

---

## Table of Contents

  1. [Intro](#intro)
  2. [Features](#features)
  3. [Module](#module)
      - [Block](#module-block)
      - [Controller](#module-controller)
  4. [Author](#author)

---

## Intro

  Visual Configurator is a Single Page Application (SPA) in Rowley project, which allows user to shop whole set of drapery products on one page. The term **visual configurator** and **product configurator** are used interchangeably.
  
  Following links are landing page for current configurators.
  - Finestra Wood (https://finestrawood.rowleycompany.com/finestra-wood-design-your-window)
  - AriA (https://aria.rowleycompany.com/aria-design-your-window)

### List of Configurators

| Finestra Wood      | AriA |
| ----------- | ----------- |
| Cord Draw Traverse System      | Stationary 1 1/8" System       |
| Cord Draw Traverse System with "C" Rings   | Stationary 1 3/8" System         |
| Baton Draw Traverse System      | H-Rail 1 1/8" System        |
| Baton Draw Traverse System with "C" Rings   | H-Rail 1 3/8" System         |
| Stationary System      | Telescoping 1 1/8" System        |



## Features


## Module

  > Detailed info about configurator module and which file does what

  - Module Level
  
    The 99% percent of configurator codes are located in module `Silk_VisualConfigurator`
    
    Shipping method related code is in `Silk/Miscellaneous/Model/Rewrite/Shipping/Shipping.php`
    
    API pricing is in module `Silk_SagePrice`
    

  <a name="module-block"></a>
  - [Block](#module-block)
  
  ~~~~
    |-- Html

        |-- Title

  ~~~~    
        `Silk\VisualConfigurator\Block\Html\Title`

        PHP class for page title template. Only used on product configurator page
      
        Set the page title on front end to be the product name
  
    |-- Product
 
        |-- View
 
            |-- Attributes

## Author

  Daniel Qin
  `daniel@maginx.com`
  
**[⬆ back to top](#table-of-contents)**
