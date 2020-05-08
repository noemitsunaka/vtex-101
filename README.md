# VTEX 101
## How to set up the sales funnel on Google Analytics?

Track and analyze the customer's steps on Google Analytics and evaluate your users’ shopping experience from product impression to transaction.

You can try to add it with a template: https://analytics.google.com/analytics/web/template?uid=tTp2GkIJRiGodszJbq8RsA

Or you can use a simple Regex to configure mannualy the sales funnel.

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
