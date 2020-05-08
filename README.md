# VTEX 101

##  How to configure Google Tag Manager on a VTEX IO store?

### Variables

* "Variables" > "User-defined variables" > "New"

#### Data Layer Variables

"Variable Configuration" > "Data Layer Variable":

* Write "userID" in "Data Layer Variable Name" > Save as "DL Variable - userID"

* Write "campaignMedium" in "Data Layer Variable Name" > Save as "DL Variable - campaignMedium"

* Write "campaignName" in "Data Layer Variable Name" > Save as "DL Variable - campaignName"

#### Google Analytics Settings

* "Variable Configuration" > "Google Analytics Settings" > Place your "Tracking ID"

* "Ecommerce" > "Enable Enhanced Ecommerce Features" > "Use data layer" > Save as "Google Analytics"

* "Fields to Set" > "Add Field":

  |  Name  |    Value   |
  |--------|------------|
  | userId | {{userId}} |

* Variable Configuration > "Google Analytics Settings" > Place your "Tracking ID" > "More Settings"

* "Fields to Set" > "Add Field":

  |     Name       |               Value              |
  |----------------|----------------------------------|
  |  campaignName  | {{DL Varibale - campaignName}}   |
  | campaignMedium | {{DL Varibale - campaignMedium}} |
  | campaignSource | {{DL Varibale - campaignSource}} |

* "Ecommerce" > "Enable Enhanced Ecommerce Features" > "Use data layer" > Save as "Google Analytics - Checkout"

### Triggers

Create different events following the path:

"Trigger Configuration" > "Custom Event"

* Save as "CE - addToCart"
* Save as "CE - email"
* Save as "CE - orderPlaced"
* Save as "CE - payment"
* Save as "CE - productDetail"
* Save as "CE - productImpression"
* Save as "CE - profile"
* Save as "CE - shipping"

### Tags

#### Pageviews

Tag Configuration > Choose Track Type "Page View":

* "Google Analytics Settings" > "{{Google Analytics}}"

Choose the Trigger:

* "All Pages"

Save as "Google Analytics - Page View"

#### Enhanced Ecommerce

"Tags" > "New" > "Tag Configuration" > "Google Analytics - Universal Analytics" > Choose Track Type "Event"

  |     Name     |               Value              |
  |--------------|----------------------------------|
  | Category     | Enhanced Ecommerce               |
  | Action       | {{Event}}                        |
  
Choose the Triggers:

* "CE - addToCart"
* "CE - email"
* "CE - orderPlaced"
* "CE - payment"
* "CE - productDetail"
* "CE - productImpression"
* "CE - profile"
* "CE - shipping"

Save as "Google Analytics - Enhanced Ecommerce"

## How to set up the sales funnel on Google Analytics?

Track and analyze the customer's steps on Google Analytics and evaluate your users’ shopping experience from product impression to transaction.

You can try to add it with a template: https://analytics.google.com/analytics/web/template?uid=tTp2GkIJRiGodszJbq8RsA

Or you can use a simple Regex to configure mannualy the sales funnel:

* Administrator > Select "Goals"

* Goal Setup > Select "Custom"

* Goal Description > Destination > Select "regular expression"

* Complete with the regular expressions below.

### Sales Funnel Regex

#### Product
```
/p($|\?)
```
#### Cart
```
^/checkout/(\?.*)?(#/cart)$
```
#### Identification
```
^/checkout/(\?.*)?#/email$
```
#### Personal Information
```
^/checkout/(\?.*)?#/profile$
```
#### Shipping Information
```
^/checkout/(\?.*)?#/shipping$
```
#### Payment
```
^/checkout/(\?.*)?#/payment$
```

## How is the traffic source of the orders different on VTEX and on Google Analytics?

Last Interaction model in Google Analytics assigns the credit to the final interaction that immediately precede conversions.

Example: A customer finds your e-commerce by clicking on a Facebook ad. Later, she returns by an Instagram stories and leave again. Next day, one of your remarketing campaigns is responsible for her going back, but she exit after open up the link. After two hours, she directly digit your website URL and makes a purchase.

On Google Analytics, the attribution will be to Direct channel because the last touchpoint before conversion was herself directly going to the website and buying something.

VTEX cookies' expire earlier than Google Analytics, that's why sometimes the traffic sources won't match.
