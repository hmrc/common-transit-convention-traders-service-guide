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

[You read more about these features](http://waitingforcontent.com)

### How we can help you with these changes

#### Available now: 
- [Review Endpoints and Error codes](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)  
- [Take advantage of tutorials](https://developer.qa.tax.service.gov.uk/api-documentation/docs/tutorials) 
- [Understand authorisation](https://developer.qa.tax.service.gov.uk/api-documentation/docs/authorisation)
- [See what you can test in our Roadmap](https://developer.qa.tax.service.gov.uk/roadmaps/common-transit-convention-traders-roadmap/#backlog)

#### Finding support

We are here to help you and answer any questions you have about the CTC API. Where you have API related questions or challenges, these will go to our developers. 

You can contact our [Software Development Support Team](mailto:sdsteam@hmrc.gsi.gov.uk) with CTC Traders API questions and support requests. They’ll find the help you need and we’ll get back to you as soon as we can. You’ll get an initial response in 2 working days. This means we’re on the case. We want to give you the best support we can. 

#### Helping you during our development phase

Please bear with us during this period of intensive development work. We will try to answer all your questions as rapidly as possible, but in some cases we may need more time during the transition from the NCTS API channel to the CTC Traders API. 

Your feedback is essential to us to build the right products, and we will direct your query to the right team to answer it. 

If you would like to take part in user research we'd like to hear from you. [Please email us.](mailto:sdsteam@hmrc.gsi.gov.uk) 


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

- [Movements Diagram](documentation/movements-diagram.html). See the end-to-end process of transporting goods using the CTC API 

## Sending an arrival message: IE007

This diagram shows how an arrival notification message is sent by the user using third party software to the NCTS, using the CTC API.

<img src="figures/sending-an-arrival-message-ie007.svg" alt="Sending an arrival notification IE007" style="width:520px;" />

1. Third party software redirects the user to the Government Gateway to get access to the CTC API.
2. Government Gateway account is authenticated and redirects the user back to 3rd party software.
3. The user sends an arrival notification message using third party software.
4. Arrival notification message passes through the CTC API.
5. Arrival notification message is received by the NCTS.
6. An accepted status is sent to the CTC API when the NCTS receives the arrival notification.
7. The accepted status passes through the CTC API.
8. The accepted status arrives at the third party software, where the user is notified the NCTS has received the arrival notification message.


<img src="figures/ctc-movements.svg" alt="CTC Movements" style="width:520px;" />


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
