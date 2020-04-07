---
title: Common Transit Convention Traders end-to-end
weight: 1
description: Software developers, designers, product owners or business analysts. Integrate your software with Common Transit Convention Traders API for Making Tax Digital.
---

# Common Transit Convention API end-to-end service guide

Version 0.1 issued 6th April 2020
***

This guide explains how you can use our Common Transit Convention (CTC) API with your software. It allows you to send and receive movement notifications and status messages to and from the New Computerised Transit System (NCTS). This API replaces the NCTS XML API Channel that is currently in use.

## Changes to the CTC API

This guide describes essential changes to the existing CTC XML API to:

- respond to changes to the NCTS system

- improve security

- accommodate the expected increase in CTC movements

The guide shows how the API fits into various end-to-end user journeys. It aims to help you understand how your software needs to interact with HMRC systems after the changes.

## Overview

UK traders can move goods freely across EU countries at the moment. This will change now the UK has left the EU. From 1 January 2021, UK traders will start moving goods under the Common Transit Convention instead. 

Common Transit Convention makes sure that traders pay the right country the right amount of tax. It means traders only pay tax for goods once they reach their final destination, rather than at each country border that the goods pass through. 

When moving goods using the Common Transit Convention, a trader will need to let the Office of Departure know that the goods have arrived at their final destination. This is done by sending an arrival notification message to the New Computerised Transit System (NCTS). 

This means that the number of goods movements being declared through the NCTS will increase. The NCTS has been upgraded already to prepare for these increases.

## Sending messages to the NCTS

You can currently send messages to the NCTS by email, web and API. The way messages can be sent to the NCTS is expected to change from 1 January 2021.

## API

The current API will not be able to cope with the increased number of messages being sent to the NCTS. Changes will be made to NCTS, including:

- removing the EDIFACT wrapper

- increasing rate limits

- moving to the cloud so it can flex with demand

- improving authorisation functionality

## Using the API

Traders who send a high number of messages and notifications should use the API.  This is because the API can accept up to 999 messages at once, whereas the web form can only accept up to 99 messages. The API will allow traders to:

- send arrival notifications to the Office of Destination

- send departure notifications to the Office of Departure


## Sending an arrival message: IE

This diagram shows how an arrival notification message is sent by the user using third party software to the NCTS, using the CTC API.

1. Third party software redirects the user to the Government Gateway to get access to the CTC API.
2. Government Gateway account is authenticated and redirects the user back to 3rd party software.
3. The user sends an arrival notification message using third party software.
4. Arrival notification message passes through the CTC API.
5. Arrival notification message is received by the NCTS.
6. An accepted status is sent to the CTC API when the NCTS receives the arrival notification.
7. The accepted status passes through the CTC API.
8. The accepted status arrives at the third party software, where the user is notified the NCTS has received the arrival notification message.

## Coming next

This diagram shows the end-to-end process of transporting goods using the Common Transit Convention API. It shows at what stage in the process each message is sent, and who each message is sent to and from.

1. Trader at departure fills in and sends a declaration notification.
2. Office of departure receives declaration notification.
3. Office of departure sends an acknowledgement of declaration notification.
4. Trader at departure receives acknowledgement notification.
5. Office of departure sends a Movement Reference Number (MRN) for the goods.
6. Trader at departure receives MRN.
7. Office of departure sends notification releasing goods for transit.
8. Office of departure receives notification releasing goods for transit.
9. Office of departure sends a notification to each Office in the countries the goods will pass through in transit.
10. Office(s) of transit receive(s) notification that goods will pass through their border.
11. Office of departure sends a notification to confirm the goods have been released for transit to their Office.
12. Office of destination receives notification that goods are on route to their Office.
13. Office(s) of transit sends a notification to confirm goods have passed through their border.
14. Office of departure receives confirmation that goods have passed through planned borders on their journey.
15. Trader at destination sends a notification to confirm that goods have arrived at their final destination.
16. Office of destination receives confirmation that goods have reached their final destination.
17. Office of destination sends a notification to confirm goods have reached their final destination.
18. Office of departure receives notification that goods have reached their final destination.
19. Office of destination sends notification that goods have passed or failed control checks.
20. Office of departure receives notification that goods have passed or failed control checks.
21. Office of departure sends notification to release the goods from the Office.
22. Trader at destination receives a notification that goods have been released.
23. Office of destination sends notification to confirm that the goods movement is complete.  This confirms that all taxes have been paid.
24. Trader at departure receives notification that the goods movement is complete. Goods are now released to be sold etc.

## Read guidance
You can learn more about the Common Transit Convention by reading guidance on

GOV.UK. In particular:

The Design Document for National Transit Application (DDNTA)

We encourage you to include links to relevant guidance in your software.

## Tell us what you think

We rely on your feedback to help us design the right APIs. Please take a few

minutes to fill in our survey.



## Related API documentation
<!--- Section owner: MTD Programme --->

  * [REST API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)
  * [Create Test User API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/api-platform-test-user/1.0)

## Changelog
<!--- Section owner: MTD Programme --->

Version 0.1

6th April 2020

What changed:

* Initial draft
