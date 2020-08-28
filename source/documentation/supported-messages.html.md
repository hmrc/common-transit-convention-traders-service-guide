# Messages we support

Here is the list of messages the CTC Traders API will support


## Arrival messages
| **Title** | **Description** |
|------|-------------|
|**Arrival notification message (IE007)**|Send an Arrival Notification message to the office at destination|
|**Arrival notification rejection (IE008)**|Get a message from the office at destination rejecting the traders Arrival Notification (IE007)|
|**Goods release notification (IE025)**|Get a message from the office at destination that the trader can release the goods|
|**Unloading permission (IE043)** |Get a message from the office at destination giving the trader permission to unload(IE043)|
|**Unloading remarks (IE044)** |Send a message to the office at desitnation containing comments in response to an unloading permission message (IE043)|
|**Unloading remarks rejection (IE058)**| Get a message rejecting unloading remarks (IE044)


|**[Get a message related to a Movement Arrival and message ID](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0#_pull-a-message-relating-to-a-movement-arrival-and-message-id_get_accordion)** |Use a message ID to get a single message|CTC Traders API
|**[Get all Movement Arrivals](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0#_pull-all-movement-arrivals_get_accordion)**|Get all messages sent within 21 days that relate to a particular trader|
|**[Send a Declaration data message (IE015)](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0#_send-a-declaration-data-message_post_accordion)**|Send a Declaration data message so a trader can start the departure process|
|**[Get a Movement Departure for a departure ID](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0#_pull-a-movement-departure-for-a-departure-id_get_accordion)** |Retrieve all mesages sent within 21 days of goods being released, relating to a Movement Departure ID|
|**[Get all messages relating to a Movement Departure](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/1.0#_pull-all-messages-relating-to-a-movement-departure_get_accordion)**| Retrieve all mesages sent within 21 days relating to a Movement Departure ID| 
