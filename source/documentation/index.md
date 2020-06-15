---
title: Common Transit Convention Traders end-to-end
weight: 1
description: Software developers, designers, product owners or business analysts. Integrate your software with Common Transit Convention Traders API.
---

# Common Transit Convention API end-to-end service guide

Version 0.2 issued 15 June 2020
***

This guide explains how you can use our new Common Transit Convention (CTC) API with your software. The API will allow your software to send and receive movement notifications and status messages to and from the EU’s New Computerised Transit System (NCTS). To trade between Europe and the UK, your software will need to change from using the NCTS XML API Channel to the CTC API, after EU exit.

### Come back for regular updates

We are updating this guide as we add more functionality to our API, new technical specifications and other items we hope you find useful. 

## Overview

UK traders can move goods freely across EU countries at the moment. This will change when the UK leaves the EU. This means there could be the possibility of paying duties and tax, where these didn’t apply before. 

From early 2021, UK traders will start moving goods under the CTC, to make sure that they pay the right country the right amount of tax for goods, only once, they reach their destination. 


### When to use the CTC API

Traders who send a high number of messages and notifications should use the API.  This is because the API can accept up to 999 messages at once, whereas the web form can only accept up to 99 messages. The API will allow traders to:

- send Arrival Notifications to the Office of Destination

- send Departure Notifications to the Office of Departure


### Why we are creating a new CTC API
It is likely that the number of goods movements being declared through the NCTS will increase. The NCTS has been upgraded already to prepare for these increases. Also, as the UK exits the EU, NCTS needs to redirect movements that involve the UK. 

We want traders to be able to seamlessly trade and send notifications to the NCTS. At the same time, we want to create an API that includes some necessary improvements. These will make it better, easier to manage and be more flexible when it’s up and running.


### Improvements that come with the new CTC API

In a nutshell, some of the improvements with the CTC API allow us to:

- respond to changes to the NCTS system
- improve security
- accommodate the expected increase in CTC movements
- make it  easier to test and maintain with an updated coding language
- move to the cloud 
- remove the EDIFACT wrapper
- monitor demand 24 hours a day to manage capacity and investigate peak flow events


### How we can help you with these changes

#### What you can do now: 
- **[Review endpoints and error codes](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)**  
- **[Take advantage of tutorials](https://developer.qa.tax.service.gov.uk/api-documentation/docs/tutorials)** 
- **[Understand authorisation](https://developer.qa.tax.service.gov.uk/api-documentation/docs/authorisation)**
- **[See what you can test in our Roadmap](https://developer.qa.tax.service.gov.uk/roadmaps/common-transit-convention-traders-roadmap/#backlog)**

#### Getting support
We have a support in place to help you with any questions or problems you might have to do with the CTC API.  
**[Find support](documentation/get-support.html)** 

#### Check service availability
Before you get in touch, check out whether API downtime or technical issues are the problem.
- **[Check the CTC Traders API service availability](https://api-platform-status.production.tax.service.gov.uk/?_ga=2.145121908.112811846.1587044117-960820992.1580203223)**    
- **[Check NCTS platform service availability](https://www.gov.uk/government/publications/new-computerised-transit-system-ncts-web-service-availability-and-issues/new-computerised-transit-system-ncts-web-service-availability-and-issues)**

 
## End-to-end process

This section shows you how the API fits into various end-to-end user journeys. It aims to help you understand how your software needs to interact with HMRC systems after the changes.


### Sending messages to the NCTS

You can currently send messages to the NCTS by email, web and API. The way messages can be sent to the NCTS is expected to change in 2021.

The current API will run at the same time as the CTC Traders API during the first part of 2021. 


## Sequence diagrams

- **[Movements diagram](documentation/movements-diagram.html)** - See the end-to-end process of transporting goods using the CTC API
- **[Sending an Arrival Notification: IE007](documentation/arrivals-diagram.html)** - See how you send an Arrival Notification to NCTS using the CTC API.  


## Read guidance
You read the full specifications for the the Common Transit Convention by reading guidance on GOV.UK. In particular:

**[The Design Document for National Transit Application (DDNTA)](https://www.gov.uk/government/publications/new-computerised-transit-system-technical-specifications)**

and the 

**[European Commission's Transition Strategy for NCTS Phase 4 to Phase 5](https://www.clecat.org/media/Transit%20transition%20strategy%20document.pdf)**

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
