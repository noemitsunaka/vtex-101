# VTEX 101
## How to set up the sales funnel on Google Analytics?
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
