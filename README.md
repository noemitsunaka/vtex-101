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

## How is the traffic source of the orders different on VTEX and on Google Analytics?

Last Interaction model in Google Analytics assigns the credit to the final interaction that immediately precede conversions.

Example: A customer finds your e-commerce by clicking on a Facebook ad. Later, she returns by an Instagram stories and leave again. Next day, one of your remarketing campaigns is responsible for her going back, but she exit after open up the link. After two hours, she directly digit your website URL and makes a purchase.

On Google Analytics, the attribution will be to Direct channel because the last touchpoint before conversion was herself directly going to the website and buying something.

VTEX cookies' expire earlier than Google Analytics, that's why sometimes the traffic sources won't match.
