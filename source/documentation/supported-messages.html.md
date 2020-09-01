# Information exchange (IE) messages we support

Here is the list of information exchange (IE) messages the CTC Traders API will support


## Departure messages
| **Title** | **Description** |
|------|-------------|
|**Declaration cancellation request (IE014)**|Send a message to cancel your declaration data (IE015) message because, for example, a duplicate entry has been made|
|**Declaration data message (IE015)**|Send a Declaration data message so a trader can start the departure process|
|**Cancellation decision message (IE009)**|Get a message from the office at departure in response to a cancellation request (IE014)|
|**Declaration data rejected (IE016)** |Get a message from the office at departure to the trader that their declaration data message (IE015) has been rejected|
|**MRN allocated (IE028)** | Get a message from the office at departure sends a Movement Reference Number to the trader at departure|
|**Release for transit (IE029)**| Get a message from the office at departure to say the goods can start their journey|
|**Write-off notification (IE045)**| Get a message from the office at departure to the trader at departure to say the movement is complete|
|**No release for transit (IE051)**| Get a message from the office at departure to the trader at departure to say the goods are not released for transit|
|**Control decision notification (IE060)**| Get a message from the office at departure to the trader at departure to say they want to carry out a control of the goods. This will come after an MRN allocated message (IE028)|
|**Positive acknowledgement message (IE928)**| Get an acknowledgement message from the office of departure that they have received a declaration data message (IE014) from the trader at departure  


## Arrival messages
| **Title** | **Description** |
|------|-------------|
|**Arrival notification message (IE007)**|Send an Arrival Notification message to the office at destination|
|**Arrival notification rejection (IE008)**|Get a message from the office at destination rejecting the traders Arrival Notification (IE007)|
|**Goods release notification (IE025)**|Get a message from the office at destination that the trader can release the goods|
|**Unloading permission (IE043)** |Get a message from the office at destination giving the trader permission to unload (IE043)|
|**Unloading remarks (IE044)** |Send a message to the office at destination containing comments in response to an unloading permission message (IE043)|
|**Unloading remarks rejection (IE058)**| Get a message rejecting unloading remarks (IE044)

