---
title: Get support and help | CTC APIs End-to-End Service Guide
weight: 3
---

# End-to-end happy path

Version 0.1 3rd June 2020
***


This diagram shows the end-to-end process of transporting goods using the Common Transit Convention API. It shows at what stage in the process each message is sent, and who each message is sent to and from.

<img src="../figures/end-to-end-happy-path.svg"/>

1.a Trader at departure fills in and sends a declaration notification IE015. 

1.b Office of departure receives declaration notification.

2.a Office of departure sends an acknowledgement of declaration 1E928.   

2.b Trader at departure receives acknowledgement notification. 

3.a Office of departure sends a Movement Reference Number (MRN) IE028.   

3.b Trader at departure receives MRN. 

4.a Office of departure sends notification releasing goods for transit IE029. 

4.b Office of departure receives notification releasing goods for transit.    

5.a Office of departure sends a notification to each office in the countries the goods will pass through in transit. This does not use the CTC Traders API.  

5.b Office or offices of transit receive notification that goods will pass through their border.   

6.a Office of departure sends a notification to confirm the goods have been released for transit. This does not use the CTC Traders API.   

6.b Office of destination receives notification that goods are on route to their Office.    

7.a Office or offices of transit sends a notification to confirm goods have passed through their border. This does not use the CTC Traders API.   

7.b Office or offices of departure receives confirmation that goods have passed through their borders.    

8.a Trader at destination sends a notification to confirm that goods have arrived at their final destination IE007. This is for simplified procedure only.    

8.b Office of destination receives confirmation that goods have reached their final destination.    

9.a Office of destination sends a notification to confirm goods have reached their final destination. This does not use the CTC Traders API.    

9.b. Office of departure receives notification that goods have reached their final destination.     

10.a Office of destination sends notification that goods have passed or failed control checks. This does not use the CTC Traders API.   

10.b Office of departure receives notification that goods have passed or failed control checks.     

11.a Office of departure sends permission that the goods can be unloaded IE043.   

11.b Trader at destination receives unloading permission.   

12.a Trader at destination sends unloading remarks about the state of the goods.    

12.b Trader a destination receives unloading remarks.   

13.a Office of departure sends notification to release the goods IE025.     

13.b Trader at destination receives a notification that goods have been released.   

14.a Office of destination sends notification to confirm that the goods movement is complete. This confirms that all taxes have been paid IE045.    

14.b Trader at departure receives notification that the goods movement is complete.  
