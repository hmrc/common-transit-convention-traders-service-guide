---

# Arrival Notifications: IE007 diagram

Version 0.1 4rd June 2020
***


This diagram shows how an arrival notification message is sent by the user using third party software to the NCTS, using the CTC API.

<img src="../figures/sending-an-arrival-message-ie007.svg"/>

Third party software redirects the user to the Government Gateway to get access to the CTC API.
Government Gateway account is authenticated and redirects the user back to 3rd party software.
The user sends an arrival notification message using third party software.
Arrival notification message passes through the CTC API.
Arrival notification message is received by the NCTS.
An accepted status is sent to the CTC API when the NCTS receives the arrival notification.
The accepted status passes through the CTC API.
The accepted status arrives at the third party software, where the user is notified the NCTS has received the arrival notification message.
