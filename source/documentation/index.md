---
title: Common Transit Convention Traders end-to-end
weight: 1
description: Software developers, designers, product owners or business analysts. Integrate your software with Common Transit Convention Traders API.
---

# Common Transit Convention Traders API end-to-end service guide

***

This guide explains how to use the new Common Transit Convention (CTC) Traders API with your software. The API will allow your software to send and receive movement notifications and status messages to and from the New Computerised Transit System (NCTS).

New CTC Traders API

* Our CTC Traders API is now live in production for GB movements only

Read our Roadmap to find out what we have planned.

## Overview

The Common Transit Convention allows traders to move goods across CTC member states without paying import duties at every border they cross. 

Under the agreement, CTC member countries only need to pay duties in the country of destination.

All goods will be subject to duties and other charges when they enter the EU, or enter the UK from the EU.

The API allows traders to send and receive arrival and departure notifications for CTC movements.


### Replacing the NCTS XML API
Volumes of Common Transit movements are expected to increase significantly now that the UK is no longer part of the European Union. The current NCTS XML API channel needs to change to cope with this forecasted increase.

In order to make sure we provide a reliable and fast service we have introduced the CTC Traders API to replace the current NCTS XML API.

**If you have never used the NCTS XML API channel, you'll only need to refer to the new CTC Traders API descriptions.**



### Comparison between the existing and the new API
The table shows how the new API uses different coding, compared to the existing NCTS XML API.  

<table>
  <tr>
    <th>Activity</th>
    <th>NCTS XML API</th>
    <th>CTC Traders API</th>
  </tr>
  <tr>
    <th>Submit Arrival Notification (IE007)</th>
    <td>SOAP authorisation (includes username and password in clear text)</td>
    <td>Government Gateway authorisation (OAuth 2.0 token)</td>
  </tr>
  <tr>
    <th>Create action</th>
    <td>SOAP wrapper, with embedded instruction</td>
    <td>RESTful interface, action inferred from the URL</td>
  </tr>
  <tr>
    <th>POST API Payload</th>
    <td>SOAP with EDIFACT body</td>
    <td>Information Exchange message (IE) XML</td>
  </tr>
  <tr>
    <th>GET API Payload</th>
    <td>SOAP with EDIFACT body</td>
    <td>JSON and IE XML</td>
  </tr>
</table>
</body>
</html>

## Payloads comparison

The diagrams show the difference between the current EDIFACT and new XML payloads for GET and POST  messages. 

<img src="./figures/post-message.png"/>

The current POST message payload consists of 4 layers:

1. Outer layer: HTTPS
2. Inside that: XML SOAP transport layer which includes 
   - WSSE authentication, consisting of a clear text username and password
   - a command (eg getDocument)
3. Within that: the EDIFACT 'wrapper' 
4. At the centre: the true payload payload which is an XML list

The new POST payload message consists of 2 layers:

1. Outer layer: RESTful standards HTTPS and OAuth 2.0 token authentication
2. At the centre: the true payload which is an XML message eg IE007

<img src="./figures/get-message.png"/>

The current GET message payload consists of 4 layers:

1. Outer layer: HTTPS 
2. WIthin that: XML SOAP transport layer, which includes 
   - WSSE authentication, consisting of clear text username and password
   - a command, eg getDocument
3. Within that: the EDIFACT 'wrapper'
4. At the centre: the true payload - the GET message

The new GET payload consists of 3 layers:

1. Outermost layer: RESTful standards HTTPS and OAuth 2.0 token authentication
2. Middle layer: a JSON list
3. At the centre: the true payload which is the XML

## Advantages of the new CTC Traders API
- Our systems will be ready for the expected increase in CTC movements
- They will greatly improve security
- Testing and maintenance of the platform will be more efficient

## What you'll need to do

### Read the documentation
[CTC Traders API specification](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0)

[CTC Testing Guide](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-testing-guide/)

[Using the Developer Hub](https://developer.service.hmrc.gov.uk/api-documentation/docs/using-the-hub)

### Testing your software
You can now test with the Trader Test service within the sandbox environment. You must not test in the live production environment.

We have published a [Guide to Testing](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-testing-guide/). This will signpost you to all the information you need and what to do.

This will include:

* all the information you need to get set up for testing
* a link to the GB test pack with scenarios and test data
* step by step guidance for how to test

Trader Test will automatically simulate and give you responses just like in a real life scenario. You can also request NCTS support staff to generate the manual responses as if Border Force staff are processing your goods. 

### Validate your XML 
Use [our XSD files](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-service-guide/documentation/xsd-reference.html) to validate your XML

### Find out which functionality we've released
Check the [roadmap](https://developer.service.hmrc.gov.uk/roadmaps/common-transit-convention-traders-roadmap/) to see what you can test now and what's coming soon.

### See the list of in-scope messages
Check which [IE messages](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-service-guide/documentation/supported-messages.html) are applicable to the CTC Traders API.

### Read about the current NCTS API channel specifications
The specifications for the current NCTS describe the business rules and logic for building software to connect with NCTS. These rules are applicable to both the current and the new APIs.

Visit the [New Computerised Transit System: technical specifications](https://www.gov.uk/government/publications/new-computerised-transit-system-technical-specifications) to read about the NCTS system that’s currently in operation.

Note, this is the specification document for the **outgoing NCTS XML API channel**, so there will be discrepancies. For example, the CTC Traders API will not use an EDIFACT wrapper or SOAP.

### Learn how to apply OAuth 2.0 
Read guidance on the [OAuth 2.0](https://developer.service.hmrc.gov.uk/api-documentation/docs/authorisation) standards required for HMRC APIs.

### Use the Developer Hub tutorials
If you're new to HMRC APIs, use the [Developer Hub tutorials](https://developer.service.hmrc.gov.uk/api-documentation/docs/tutorials) to find out what you need to know about working with us.

## Get help

We have support in place to help you with any questions or problems you might have with the CTC Traders API. [Find out to get help](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-service-guide/documentation/get-support.html).

## Check service availability

Before you get in touch, check out whether API downtime or technical issues are the problem. [Check the HMRC API platform availability.](https://api-platform-status.production.tax.service.gov.uk/)

## End-to-end process

The steps you need to take before you can use your software in the live environment:

1. **Register and subscribe to the Developer Hub**
[Register for a developer account](https://developer.service.hmrc.gov.uk/developer/registration) and subscribe to the CTC Traders API, Create Test User API and CTC PUSH/PULL notifications (to be released in February).
2. **Understand Government Gateway authorisation**
In order to use the CTC Traders API your software needs to interact [using OAuth 2.0](https://developer.service.hmrc.gov.uk/api-documentation/docs/authorisation).
3. **Create test user**
To start testing your software, you need to generate [test users](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/api-platform-test-user/1.0).
4. **Download reference data**
To get Customs Offices List (COL) data to use for testing, [visit the EU’s reference data download page](https://ec.europa.eu/taxation_customs/dds2/col/col_download_home.jsp?Lang=en).
5. **Apply to go live**
You need to apply for production credentials through your [developer account](https://developer.service.hmrc.gov.uk/developer/login).
6. **Get your customers ready**
For example, ask them to apply for an [EORI number](https://www.gov.uk/eori) and a [Government Gateway account](https://www.gov.uk/log-in-register-hmrc-online-services).

## Northern Ireland transit

Following the end of the UK's transition from the EU, Northern Ireland transit movements (or NI movements) are handled slightly differently by the NCTS.

You can use the existing EDIFACT API channel and the email channel to submit departure and arrival messages for Northern Ireland  NCTS instances. EDIFACT API messages will automatically be routed to the appropriate NCTS system without you having to make any changes to your software.

We expect the CTC Traders API to support Northern Ireland (NI) movements from late April 2021. The exact date will be published in our [Roadmap](https://developer.service.hmrc.gov.uk/roadmaps/common-transit-convention-traders-roadmap/) and we will email everyone who is subscribed to the CTC Traders API as soon it is available.

## Message flows

Review the message flow diagrams to see the correct message sequences:

- [End-to-end happy path diagram](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-service-guide/documentation/end-to-end-happy-path.html) - the end-to-end process of transporting goods using the CTC Traders API
- [Sending an Arrival Notification diagram](https://developer.service.hmrc.gov.uk/guides/common-transit-convention-traders-service-guide/documentation/arrivals-diagram.html) - for sending an Arrival Notification to NCTS using the CTC Traders API

## Changelog

Version 0.5: 31 March 2021
Added revised bullet point information about CTC Traders API go live plus NI functionality planned to go live around April 2021.

Version 0.4: 10 February 2021
Added release date for the GB version of the API.

Version 0.3 11 September 2020
Added more XSD files and added to list of supported IE messages.

Version 0.2: 6 August 2020
Added further detail in reference to the XSD files.

Version 0.1: 15 July 2020
First release
