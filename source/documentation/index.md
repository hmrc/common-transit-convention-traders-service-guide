---
title: Common Transit Convention Traders end-to-end
weight: 1
description: Software developers, designers, product owners or business analysts. Integrate your software with Common Transit Convention Traders API.
---

# Common Transit Convention API end-to-end service guide

Version 0.2 issued 2nd June 2020
***

This guide explains how you can use our new Common Transit Convention (CTC) APIs with your software. The API will allow you to send and receive movement notifications and status messages to and from the EU’s New Computerised Transit System (NCTS). Traders will move from using the NCTS XML API Channel to CTC APIs, after EU exit.

### Come back for regular updates

We are updating this guide as we add more functionality to our APIs, new technical specifications and other items we hope you find useful. These could include video guides and more sequence diagrams. 

Tell us what you need and we will try and make it happen. Email our [Software Development Support Team](mailto:sdsteam@hmrc.gsi.gov.uk)

## Overview

UK traders can move goods freely across EU countries at the moment. This will change when the UK leaves. This means possibly paying duties and tax, where this didn’t apply before. From early 2021, UK traders will start moving goods under the CTC instead, to make sure that they pay the right country the right amount of tax for goods, once they reach their destination. 

When moving goods using the Common Transit Convention, a trader will need to let the Office of Departure know that the goods have arrived at their final destination. This is done by sending an arrival notification message to the New Computerised Transit System (NCTS). 

It is likely that the number of goods movements being declared through the NCTS will increase. The NCTS has been upgraded already to prepare for these increases. 


### Why we are changing to the new CTC API

The NCTS is changing because the UK is leaving the UK. So we have to make changes in our API as well. But, at the same time, we’re making some improvements. We want to make it better, easier to manage and be more flexible, when it’s up and running.


### Improvements that come with the new CTC API

In a nutshell, some of the improvements with the CTC API allow us to:

- respond to changes to the NCTS system
- improve security
- allow for accommodate the expected increase in CTC movements
- be easier to test and maintain with an updated coding language
- move to the cloud 
- remove the EDIFACT wrapper
- monitor demand 24 hours a day to manage and investigate peak flow events


### How we can help you with these changes

#### What you can do now: 
- [Review Endpoints and Error codes](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)  
- [Take advantage of tutorials](https://developer.qa.tax.service.gov.uk/api-documentation/docs/tutorials) 
- [Understand authorisation](https://developer.qa.tax.service.gov.uk/api-documentation/docs/authorisation)
- [See what you can test in our Roadmap](https://developer.qa.tax.service.gov.uk/roadmaps/common-transit-convention-traders-roadmap/#backlog)

#### Getting support
We have a support in place to help you with any questions or problems you might have to do with the CTC APIs: 
- [Find support](documentation/get-support.html)and see how we can support you
- [Check our service availability](https://api-platform-status.production.tax.service.gov.uk/?_ga=2.145121908.112811846.1587044117-960820992.1580203223) before you get in touch, in case a downtime or technical issues are the problem.
 
## End-to-end process

The rest of this guide shows how the API fits into various end-to-end user journeys. It aims to help you understand how your software needs to interact with HMRC systems after the changes.


### Sending messages to the NCTS

You can currently send messages to the NCTS by email, web and API. The way messages can be sent to the NCTS is expected to change in 2021.

The current API will run at the same time as the updated API for a short while. 


### When to use the API

Traders who send a high number of messages and notifications should use the API.  This is because the API can accept up to 999 messages at once, whereas the web form can only accept up to 99 messages. The API will allow traders to:

- send Arrival Notifications to the Office of Destination

- send Departure Notifications to the Office of Departure


## Sequence Diagrams

- [Movements Diagram](documentation/movements-diagram.html) - See the end-to-end process of transporting goods using the CTC API 
- [Sending an Arrival Notification: IE007](documentation/arrivals-diagram.html) - See how you send an Arrival Notification to NCTS using the CTC API.  


## Read guidance
You can learn more about the Common Transit Convention by reading guidance on GOV.UK. In particular:

[The Design Document for National Transit Application (DDNTA)](https://www.gov.uk/government/publications/new-computerised-transit-system-technical-specifications)

and the 

[European Commissions Transition Strategy for NCTS Phase 4 to Phase 5](https://www.clecat.org/media/Transit%20transition%20strategy%20document.pdf).

We encourage you to include links to relevant guidance in your software.





## Related API documentation
<!--- Section owner: MTD Programme --->

  * [REST API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)
  * [Create Test User API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/api-platform-test-user/1.0)

## Changelog
<!--- Section owner: MTD Programme --->

Version 0.2

2 May 2020

What changed:

* Second draft.
