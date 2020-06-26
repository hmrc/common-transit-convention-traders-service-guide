---
title: Common Transit Convention Traders end-to-end
weight: 1
description: Software developers, designers, product owners or business analysts. Integrate your software with Common Transit Convention Traders API.
---

# Common Transit Convention API end-to-end service guide

Version 0.2 issued 15 June 2020
***

This guide explains how you can use our new Common Transit Convention (CTC) API with your software. The API will allow your software to send and receive movement notifications and status messages to and from the EU’s New Computerised Transit System (NCTS). 

To trade between Europe and the UK, your software will need to change from using the NCTS XML API Channel to the CTC API, after EU exit.

### Come back for regular updates

We are updating this guide as we add more functionality to our API, new technical specifications and other items we hope you find useful. 

## Overview

Right now, goods that can move freely  within the UK can move across the EU without restriction. This will change after the end of the transition period on 31 December 2020. Then, those goods will be subject to duties and other charges when they enter the EU.

From 2021, if UK traders want to defer paying these duties and other charges, they can move the goods under Common Transit Convention. This will allow traders to move goods across a number of countries, without having to pay import duties every time they cross a border. They will only have to complete the paperwork and pay any duties they owe, once they reach their destination country.



### When to use the CTC API

Traders who make a significant number of Transit declarations may prefer to use the CTC API. It will  allow up to 999 items per declaration as opposed to 99 items via the web portal. It also means large scale traders can create bespoke software solutions. 

The API will allow traders to:

- send Arrival Notifications to the Office of Destination

- send Departure Notifications to the Office of Departure


### Why we are creating a new CTC API

We believe Common Transit will be a key procedure for moving goods between the United Kingdom and Europe. We expect that declaration volumes will increase significantly. In order to make sure we provide a reliable and fast service we are introducing the new CTC API to replace the current XML channel API.


### Improvements that come with the new CTC API

Essentially the improvements the CTC API will bring are:
- seamless handling of changes to the NCTS core\
- removing the EDIFACT wrapper\ 
- improving security\
- being ready for  the expected increase in CTC movements\ 
- making it easier to test and maintain with an updated coding language\  
- allowing  cloud hosting of our systems\
- monitoring demand 24 hours a day to manage capacity and investigate peak flow events 



### How we can help you with these changes

#### What you can do now: 
- **[Review endpoints and error codes](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)**  
- **[Take advantage of tutorials](https://developer.qa.tax.service.gov.uk/api-documentation/docs/tutorials)** 
- **[Understand authorisation](https://developer.qa.tax.service.gov.uk/api-documentation/docs/authorisation)**
- **[See what you can test in our roadmap](https://developer.qa.tax.service.gov.uk/roadmaps/common-transit-convention-traders-roadmap/#backlog)**

#### Find support
We have a support in place to help you with any questions or problems you might have to do with the CTC API. [Get intouch](documentation/get-support.html) and we'll get right back to you. 


#### Check service availability
Before you get in touch, check out whether API downtime or technical issues are the problem:
- **[Check the CTC Traders API service availability](https://api-platform-status.production.tax.service.gov.uk/?_ga=2.145121908.112811846.1587044117-960820992.1580203223)**    
- **[Check NCTS platform service availability](https://www.gov.uk/government/publications/new-computerised-transit-system-ncts-web-service-availability-and-issues/new-computerised-transit-system-ncts-web-service-availability-and-issues)**

 
## End-to-end process

This section shows you how the API fits into various end-to-end user journeys. It aims to help you understand how your software needs to interact with HMRC systems after the changes.


### Get authorisation from Government Gateway to use the API

In order to use CTC Traders API your software needs to interact with the Government Gateway to [get authorisation](https://developer.service.hmrc.gov.uk/api-documentation/docs/authorisation/user-restricted-endpoints).


### Get an EORI number to do business with the EU

To trade with the EU after the UK leaves, traders will need to [get an EORI number](https://www.gov.uk/eori).


### When these changes are happening 

We will release the new CTC Traders API into the NCTS production environment on 31 December 2020.

### What's happening for Northern Ireland transit

From 1 January 2021, the submission channel for Northern Ireland departure and arrival notification messages will be by email only. This is an interim solution while work continues to enable the new API to also serve Northern Ireland. We will share further information about this in the future.


## Journey diagrams
Below are two simplified diagrams that give you an overview of the new processes involving the CTC Traders API:

- **[Movements diagram](documentation/movements-diagram.html)** - See the end-to-end process of transporting goods using the CTC API
- **[Sending an Arrival Notification: IE007](documentation/arrivals-diagram.html)** - See how you send an Arrival Notification to NCTS using the CTC API.  


## Full specifications
You read the full specifications for the Common Transit Convention by reading:

- **[NCTS Phase 4 Technical Interface Specification (TIS)](https://www.gov.uk/government/publications/new-computerised-transit-system-technical-specifications)**. (this will be updated after 31 December 2020)   
- **[European Commission's Transition Strategy for NCTS Phase 4 to Phase 5](https://www.clecat.org/media/Transit%20transition%20strategy%20document.pdf)**

We encourage you to include links to relevant guidance in your software.





## Related API documentation
<!--- Section owner: MTD Programme --->

  **[REST API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)**  
  **[Create Test User API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/api-platform-test-user/1.0)**

## Changelog
<!--- Section owner: MTD Programme --->

Version 0.2

15 June 2020

What changed:

* Second draft.
