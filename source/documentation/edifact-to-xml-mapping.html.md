---
title: EDIFACT to XML mapping | CTC APIs End-to-End Service Guide
weight: 3
---


# EDIFACT to XML mapping

## **Key - read this first**

Column name | Description
---|---
**SAD box** | The number of the corresponding box on the [Single Administrative Document](https://ec.europa.eu/taxation_customs/business/customs-procedures/general-overview/single-administrative-document-sad_en) for this data item. These columns are only shown for the CUSDEC and CUSRES correlation tables.  
**Message element** | The full name of the data item, in plain language
**Data type** | The format of the data type
**Data requirements** |R - required     O - optional    D - dependent
**EDIFACT Position** | The position of the EDIFACT-segment in the UNSM. This position refers to the branching diagram on chapter not 5 **Oli?** of our [Technical Interface Specifations](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/641488/NCTSPhase4TISv3_9_3.pdf)
**EDIFACT mapping** | The mapping information for a an EDIFACT segment
**XML mapping** | The mapping information for an XML segment
**Code list**| For the code list references (number only)- see Appendix C
**Condition/rules** | C - Conditions for IE messages (see Appendix C); R - Structure Rules for IE messages (See Appendix D); TR - Technical Rules for IE messages (See Appendix E)

**LNG** = language


## Arrival notification (IE007 - E_ARR_NOT)
(Scroll right to see the whole table)


**SAD Box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | | |
|| **HEADER** | | **R**| -- | | **HEAHEA**| | |
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| - | -
||Customs sub place | an..17|D| 4 |LOC[4] \(3227=26).C517.3225| CusSubPlaHEA66|  - | C155, R245
||Arrival notification place | an..35|R| 4 |LOC[4] \(3227=60).C517.3224| ArrNotPlaHEA60| - | -
||Arrival notification place LNG | a2 |O| 4 |LOC[4] \(3227=60).5479| ArrNotPlaHEA60LNG| 12 | TR99
||Arrival agreed location code | an..17|D| 4 |LOC[4] \(3227=20).C517.3225| ArrAgrLocCodHEA62| - | C155, R245
||Arrival agreed location of goods | an..35|D| 4 |LOC[4] \(3227=20).C517.3224| ArrAgrLocOfGooHEA63| - | C155, R245
||Arrival agreed location of goods LNG | a2|O| 4 |LOC[4] \(3227=20).5479| ArrAgrLocOfGooHEA63LNG| 12 | TR99
||Arrival authorised location of goods | an..17 |D| 4 |LOC[4] \(3227=84).C517.3225| ArrAutLocOfGooHEA65| - | C155, R245
||Simplified procedure flag | n1 |R| 6 |GIS[6] \(C529.1131=119).C529.7365| SimProFlaHEA132| 27 |  R230
||Arrival notification date | n8 |R| 5 |DTM[5] \(C507.2005=132).C507.2380| ArrNotDatHEA141| - | -
||Dialog language indicator at destination | a2 |O| 11 |FTX[11] \(4451=ACB).3453| DiaLanIndAtDesHEA255| 12 | -

(Scroll right to see the whole table)   

**SAD Box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DESTINATION) TRADER** | | **R**| -- | | **TRADESTRD**| | |
|| Name |an..35 |D| 22 |NAD[22] \(3035=CPD).C080.3036#1| NamTRD7|  - | C160
||Street and number |an..35 |D| 22 |NAD[22] \(3035=CPD).C059.3042#1| StrAndNumTRD22| - | C160
||Postal code |an..9 |D| 22 |NAD[22] \(3035=CPD).3251| PosCodTRD23|- | C160
||City |an..35 |D| 22 |NAD[22] \(3035=CPD).3164| CitTRD24|- | C160
||Country code |a2 |D| 22 |NAD[22] \(3035=CPD).3207 |CouTRD25|8 | C160
||NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CPD).3229 |NADLNGRD|12 | TR99
||EORI-TIN (Turn) |an..17 |D| 22 |NAD[22] \(3035=CPD).3039 | TINTRD59 |- | C112|

(Scroll right to see the whole table)     

**SAD Box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRESENTATION OFFICE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFPREOFFRES**| ||
|| Reference number |a8 |R| 4 |LOC[4] \(3227=22).C517.3225|RefNumRES1|-|-

(Scroll right to see the whole table)     

**SAD Box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **EN ROUTE EVENT occurs 9** | | **O**| -- | | **ENROUEVETEV**| - | **R240**|
||Place |an..35 |R| 12 |RFF[12]\(C506.1153=AIV).C506.1154|PlaTEV10|-| -
||Place LNG |a2 |O| 12 |RFF[12]\(C506.1153=AIV).C506.1156|PlaTEV10LNG|12 | TR99|
||Country code |a2 |R| 14 |RFF(C506.1153=AIV).PAC[14] \(7224=2).C402.7077|CouTEV13|9 | -|
||**CTL_CONTROL** | | **R**| **--** | | **CTLCTL**|  | |
||CTL_CONTROL Already in NCTS |nl |R| 13 |RFF(C506.1153=AIV).DTM[13] \(C507.2005=311).C507.2380|AlrInNCTCTL29|27 | R230|
||**INCIDENT** | | **O**| **--** | | **INCINC**| - | **R240**  |
||INCIDENT Incident flag |nl |C| 14 |RFF(C506.1153=AIV).PAC[14] \(7224=3) .C531.7075|IncFlaINC3|27 | R230, TR9030|
||INCIDENT Incident information |an..350 |O| 16 |RFF(C506.1153=AIV).PAC(7224=3).PCI(4233=18).FTX[16] \(4451=ABM).C108.4440#1|IncInfINC4|-| -
||INCIDENT Incident information LNG |a2 |O| 16 |RFF(C506.1153=AIV).PAC(7224=3).PCI(4233=18).FTX[16] \(4451=ABM).3453|IncInfINC4LNG|12 | TR99|
||INCIDENT Endorsement date |n8 |O| 15 |RFF(C506.1153=AIV).PAC(7224=3).PCI[15] \(4233=18).C210.7102#1| EndDatINC6|-|-
||INCIDENT Endorsement authority |an..35 |O| 15 |RFF(C506.1153=AIV).PAC(7224=3).PCI[15] \(4233=18).C210.7102#2| EndAutINC7|-|-
||INCIDENT Endorsement authority LNG |a2 |O| 15 |RFF(C506.1153=AIV).PAC(7224=3).PCI[15] \(4233=18).C210.7102#3| EndAutINC7LNG|12 | TR99|
||INCIDENT Endorsement place |an..35 |O| 15 |RFF(C506.1153=AIV).PAC(7224=3).PCI[15] \(4233=18).C210.7102#4| EndPlaINC10|-|-
||INCIDENT Endorsement place LNG |a2 |O| 15 |RFF(C506.1153=AIV).PAC(7224=3).PCI[15] \(4233=18).C210.7102#5| EndPlaINC10LNG|12 | TR99|
||INCIDENT Endorsement country |a2 |O| 15 |RFF(C506.1153=AIV).PAC(7224=3).PCI[15] \(4233=18).C210.7102#6| EndCouINC12|9 | - |
||**SEALS INFO** | | **O**| **--** | | **SEAINFSF1**| - | **R240**  |
||SEALS INFO Seals number |n4 |R| 14 |RFF(C506.1153=AIV).PAC[14] \(7224=4).C402.7077| SeaNumSF12|- |-
|| **SEALS INFO - SEALS ID occurs 99** | | **R**| **--** | | **SEAIDSI1**| - | -
||SEALS INFO - SEALS ID Seals identity |an..20 |R| 15 |RFF(C506.1153=AIV).PAC(7224=4).PCI[15] \(4233=21).C210.7102#1| SeaIdeSI11|- | -
||SEALS INFO - SEALS ID Seals identity LNG  |a2 |O| 15 |RFF(C506.1153=AIV).PAC(7224=4).PCI[15] \(4233=21).C210.7102#2| SeaIdeSI11LNG|12 | TR99 |
|| **TRANSHIPMENT** | | **O**| **--** | | **TRASHP**| - | **R240**
|55|TRANSHIPMENT New transport means identity |an..27 |0| 16 |RFF(C506.1153=AIV).PAC(7224=5).PCI(4233=23).FTX[16] \(4451=TRA).C108.4440#1| NewTraMeaIdeSHP26|- | R190
||TRANSHIPMENT New transport means identity LNG |a2 |0| 16 |RFF(C506.1153=AIV).PAC(7224=5).PCI(4233=23).FTX[16] \(4451=TRA).3453|NewTraMeaIdeSHP26LNG|12 | TR99 |
|55|TRANSHIPMENT New transport means nationality |a2 |0| 14 |RFF(C506.1153=AIV).PAC[14] \(7224=5).C202.7064 | NewTraMeaNatSHP54 |8 | R190 |
||TRANSHIPMENT Endorsement date |n8 |0| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=23).C210.7102#1 | EndDatSHP60 |- |-
||TRANSHIPMENT Endorsement authority |an..35 |0| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=23).C210.7102#2 | EndAutSHP61 |- |-
||TRANSHIPMENT Endorsement authority LNG |a2 |0| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=23).C210.7102#3 | EndAutSHP61LNG | 12 | TR99 |
||TRANSHIPMENT Endorsement place |an..35 |0| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=23).C210.7102#4 | EndPlaSHP63 | - |-
||TRANSHIPMENT Endorsement place LNG |a2 |0| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=23).C210.7102#5| EndPlaSHP63LNG | 12 | TR99 |
|| TRANSHIPMENT Endorsement country |a2 |0| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=23).C210.7102#6 | EndCouSHP65 | 9 | - |
|| **TRANSHIPMENT - CONTAINERS occurs 99** | | **O**| **--** | | **CONNR3**| - |-
|| TRANSHIPMENT - CONTAINERS Container number |an..17 |R| 15 |RFF(C506.1153=AIV).PAC(7224=5).PCI[15] \(4233=30).C210.7102#1| ConNumNR31 | - | R190

## Arrival notification rejection (IE08 - E_ARR_REJ)
(Scroll right to see the whole table)


**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK** | **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | ||
|| **HEADER** | | **R**| -- | | **HEAHEA**| | |
|| Document/reference number (MRN)|an..21 |R| 2 |BGM[2]  \(1225=11).C106.1004 | DocNumHEA5| - | -
|| Arrival rejection date |n8 |R| 3 |DTM[3] \(C507.2005=46).C507.2380 | ArrRejDatHEA142| - | -
|| Action to be taken |an..350 |O| 4 |FTX[4] \(4451=ABD).C108.4440#1 | ActToBeTakHEA238| - | -
|| Action to be taken LNG |a2 |O| 4 |FTX[4] \(4451=ABD).3453 | ActToBeTakHEA238LNG| 12 | TR99
|| Arrival rejection reason |an..350 |O| 4 |FTX[4] \(4451=ARR).C108.4440#1 | ArrRejReaHEA242| - | -
|| Arrival rejection reason LNG |a2 |O| 4 |FTX[4] \(4451=ARR).3453 | ArrRejReaHEA242LNG| 12 | TR99

(Scroll right to see the whole table)   

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
| | **FUNCTIONAL ERROR occurs 999** | | **D**| -- | | **FUNERRER1**| - | **R123** |
|| Error type |n2 | R | 4 |FTX[4] \(4451=AAO).C107.4441 |ErrTypER11| 49 | -
||Error pointer |an..210 | R | 4 |FTX[4] \(4451=AAO).C108.4440#1 |ErrPoiER12| 100- | -
|| Error reason |an..6 | O | 4 |FTX[4] \(4451=AAO).C108.4440#4 |ErrReaER13| - | -
|| Original attribute value |an..140 | O | 4 |FTX[4] \(4451=AAP).C108.4440#1 |OriAttValER14| - | -

## Cancellation decision (IE009 - E_CAN_DEC)
(Scroll right to see the whole table)


**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | | |
|| **HEADER** | | **R**| -- | | **HEAHEA**| | |
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2]  \(1225=11).C106.1004 | DocNumHEA5| - | -
||Cancellation decision| n1 |D| 7 |GIS[7] \(C529.1131=70).C529.7365 |CanDecHEA93| 27 | C170, R180, R230
||Date of cancellation request| n8 |D| 3 |DTM[3] \(C507.2005=318).C507.2380 |DatOfCanReqHEA147| - | C180
||Cancellation initiated by Customs| n1 |R| 7 |GIS[7] \(C529.1131=117).C529.7365 |CanIniByCusHEA94| 27 | R175, R230
||Date of cancellation decision| n8 |R| 3 |DTM[3] \(C507.2005=193).C507.2380 |DatOfCanDecHEA146| - | -
||Cancellation justification| an..350 |D| 4 |FTX[4] \(4451=ABY).C108.4440#1 |CanJusHEA248| - | C175
||Cancellation justification LNG| a2 |O| 4 |FTX[4] \(4451=ABY).3453 |CanJusHEA248LNG | 12 | TR99

(Scroll right to see the whole table)   

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| -- | | **TRAPRIPC1**| ||
|50| Name |an..35 |D| 9 |NAD[9] \(3035=AF).C080.3036#1| NamPC17|  - | C160
|50|Street and number |an..35 |D| 9 |NAD[9] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C160
|50|City |an..35 |D| 9 |NAD[9] \(3035=AF).3164| CitPC124|- | C160
|50|Country code |a2 |D| 9 |NAD[9] \(3035=AF).3207 |CouPC125|8 | C160
|50|NAD_LNG |a2 |O| 9 |NAD[9] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |D| 9 |NAD[9] \(3035=AF).C082.3039 |TINPC159|- | R012, R174|
|50|Holder ID TIR |an..17 |D| 9 |NAD[9] \(3035=AF).C080.3036#2 |HITPC126|- | C904|

(Scroll right to see the whole table)   

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
| | **(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| | |
| | Reference number |an8 |R| 6 |LOC[6] \(3227=118).C517.3225 |RefNumEPT1|- | -

## Declaration cancellation request (IE014 - E_DEC_CAN)

<details>
  <summary>**See IE014 details**</summary>

(Scroll right to see the whole table)   

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
| | **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |
| | **HEADER** | | **R**| -- | | **HEAHEA**| | |
| | Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| - | -
| | Date of cancellation request| n8 |R| 5 |DTM[5] \(C507.2005=318).C507.2380 |DatOfCanReqHEA147| - |-
| | Cancellation reason| an..350|R| 11 |FTX[11] \(4451=ACD).C108.4440#1 |CanReaHEA250| - |-
| | Cancellation reason LNG| a2 |O| 11 |FTX[11] \(4451=ACD).3453|CanReaHEA250LNG| 12 | TR99

(Scroll right to see the whole table)  

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
| | **(PRINCIPAL) TRADER** | | **R**|-- | | **TRAPRIPC1**| | |
|50 | Name |an..35 |D| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  - | C160
|50 |Street and number |an..35 |D| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C160
| 50 |Postal code |an..9 |D| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|- | C160
| 50 |City |an..35 |D| 22 |NAD[22] \(3035=AF).3164| CitPC124|- | C160
| 50 |Country code |a2 |D| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8 | C160
| 50 |NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
| 50 |EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | R174
| 50 |Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904

(Scroll right to see the whole table)  

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
| | **(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| ||
| | Reference number |an8 |R| 4 |LOC[4] \(3227=118).C517.3225 |RefNumEPT1|- |-
</details>

## Declared data (IE015 - E_DEC_DAT)
(Scroll right to see the whole table)


**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** | | **R** | -- | | ||
|| Syntax identifier |a4 |R| 0 |UNB[0].S001.0001 |SynIdeMES1|21 | -
|| Syntax version number |nl |R| 0 |UNB[0].S001.0002 |SynVerNumMES2|22 | -
|| Message sender |an..35 |R| 0 |UNB[0].S002.0004 |MesSenMES3| - |-
|| Message recipient |an..35 |R| 0 |UNB[0].S003.0010 |MesRecMES6| -|-
|| Date of preparation |n6 |R| 0 |UNB[0].S004.0017 |DatOfPreMES9| -|-
|| Time of preparation |n4 |R| 0 |UNB[0].S004.0019 |TimOfPreMES10| -|-
|| Interchange control reference |an..14 |R| 152 |UNZ[152].0020 |IntConRefMES11| -|-
|| Interchange control reference |an..14 |R| 0|UNB[0].0020|| -|-
|| Application reference |an..14 |R| 0|UNB[0].0026|AppRefMES14 | -|-
|| Priority |a1 |O| 0|UNB[0].0029|PriMES15 | -|-
|| Acknowledgement request |n1 |O| 0|UNB[0].0031|AckReqMES16 | 27 | -
|| Communications agreement ID |an..35 |O| 0|UNB[0].0032|ComAgrIdMES17 | -|-
|| Test indicator |n1 |O| 0|UNB[0].0035|TesIndMES18 | - | TR9085
|| Message identification |an..14 |R| 151|UNT[151].0062|MesIdeMES19 | -|-
|| Message identification |an..14 |R| 1|UNH[1] \(S009.0065=CUSDEC)(S009.0052=D)(S009.0054=96B)(S009.0051=UN).0062| | -|-
|| Message type |an..6 |R| 1|UNH[1] \(S009.0065=CUSDEC)(S009.0052=D)(S009.0054=96B)(S009.0051=UN).S009.0057| MesTypMES20| 60 | -
|| Common access reference |an..35 |0| 1|UNH[1] \(S009.0065=CUSDEC)(S009.0052=D)(S009.0054=96B)(S009.0051=UN).0068| ComAccRefMES21| -|-
|| Number of segments (exc.UNB and UNZ) in the message|n..6 |R| 151|UNT[151].0074| | -|-
|| Number of messages in the interchange|n..6 |R| 152|UNZ[152].0036| | -|-

(Scroll right to see the whole table)   

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
|7|Reference number (LRN)|an..22 |R| 12|RFF[12] \(C506.1153=ABE).C506.1154|RefNumHEA4 | - |-
|1|Type of declaration|an..9 |R| 2|BGM[2].C002.1000|TypOfDecHEA24 | 31 | R909, R911
|17a| Country of destination code|a2 |D| 4|LOC[4] \(3227=36).C517.3225|CouOfDesCodHEA30 | 8 | C140
|30| Agreed location of goods, code|an..17 |D| 4|LOC[4] \(3227=14).C517.3225|AgrLocOfGooCodHEA38 | - | C100, R41
|30|Agreed location of goods|an..35 |D| 4|LOC[4] \(3227=14).C517.3224|AgrLocOfGooHEA39 | - | C100, R41
||Agreed location of goods LNG|a2 |O| 4|LOC[4] \(3227=14).5479|AgrLocOfGooHEA39LNG | 12 | TR99
|30| Authorised location of goods, code|an..17 |D| 4|LOC[4] \(3227=14).C519.3223|AutLocOfGooCodHEA41 | - | C100, R41
|27|Place of loading, code|an..17 |D| 4|LOC[4] \(3227=9).C517.3225|PlaOfLoaCodHEA46 | - | C191
|15A|Country of dispatch/export code|a2 |D| 4|LOC[4] \(3227=35).C517.3225|CouOfDisCodHEA55 | 8 | C135
||Customs sub place|an..17 |D| 4|LOC[4] \(3227=26).C517.3225|CusSubPlaHEA66 | - | C100, R41
|26| Inland transport mode|n..2 |O| 17|TDT[17] \(8051=1).C220.8067| InlTraModHEA75 | 18 | -
|25|Transport mode at border|n..2 |D| 17|TDT[17] \(8051=11).C220.8067| TraModAtBorHEA76 | 18 | C599
|18|Identity of means of transport at departure (exp/trans)|an..27 |D|17 |TDT[17] \(8051=12).C222.8212| IdeOfMeaOfTraAtDHEA78 | - | TR0035, TR9090
||Identity of means of transport at departure LNG|a2 |O|18 |TDT(8051=12).TPL[18].C222.8453| IdeOfMeaOfTraAtDHEA78LNG | 12 | TR99
|18|Nationality of means of transport at departure|a2 |D|17 |TDT[17] \(8051=12).C222.8453| NatOfMeaOfTraAtDHEA80 | 8 | TTR0035, TR9095
|21|Identity of means of transport crossing border|an..27 |D|17 |TDT[17] \(8051=11).C222.8212| IdeOfMeaOfTraCroHEA85 | - | C011
||Identity of means of transport crossing border LNG|a2 |O|18 |TDT(8051=11).TPL[18].C222.8453| IdeOfMeaOfTraCroHEA85LNG |12 | TR99
|21|Nationality of means of transport crossing border|a2 |D|17 |TDT[17] \(8051=11).C222.8453| NatOfMeaOfTraCroHEA87 |8 | R36, C10
||Type of means of transport crossing border|n..2 |O|17 |TDT[17] \(8051=11).C228.8179| TypOfMeaOfTraCroHEA88 |18 | -
|19| Containerised indicator|n1 |R|6 |GIS[6] \(C529.1131=109).C529.7365| ConIndHEA96 |27 | R230
|| Dialog language indicator at departure|a2 |O|11 |FTX[11] \(4451=ACB).3453| DiaLanIndAtDepHEA254 |12 | R100
|| NCTS accompanying document language code|a2 |R|11 |FTX[11] \(4451=ALL).3453| NCTSAccDocHEA601LNG |12 | -
|5| Total number of items|n..5 |R|145 |CNT[145] \(C270.6069=5).C270.6066| TotNumOfIteHEA305 | - |-
|6|Total number of packages|n..7 |O|145 |CNT[145] \(C270.6069=11).C270.6066| TotNumOfPacHEA306 | - | R105
|35|Total gross mass|n..11,3 |R|8 |MEA[8] \(6311=WT)(C502.6313=AAD)(C174.6411=KGM).C174.6314| TotGroMasHEA307 | -|-
|50|Declaration date|n8 |R|5 |DTM[5] \(C507.2005=137).C507.2380| DecDatHEA383 | - |-
|50|Declaration place|an..35 |R|4 |LOC[4] \(3227=91).C517.3224| DecPlaHEA394 | -|-
|50|Declaration place LNG|a2 |O|4 |LOC[4] \(3227=91).5479| DecPlaHEA394LNG | 12 | TR99
||Specific Circumstance Indicator|a1 |D|12 |RFF[12] \(C506.1153=AMJ).C506.1154| SpeCirIndHEA1 | 96 | C186, R825
||Transport charges/ method of payment|a1 |D|11 |FTX[11] \(4451=PAI).4453| TraChaMetOfPayHEA1 | 116 | C186
||Commercial reference number|an..70 |D|7 |FII[7] \(3035=XX).C088.3436| ComRefNumHEA | - | C186, C547, R876
||Security|n1 |O|6 |GIS[6] \(C529.1131=187).C529.7365| SecHEA358 | 117 | R229
||Conveyance reference number|an..35 |O|11 |FTX[11] \(4451=ACR).C108.4440#1| ConRefNumHEA | - | C531
||Place of unloading, code|an..35 |D|4 |LOC[4] \(3227=58).C517.3224| CodPlUnHEA357 | - | C186, C589
||Place of unloading, LNG|a2 |O|4 |LOC[4] \(3227=58).C517.3225| CodPlUnHEA357LNG | 12 | TR0099


(Scroll right to see the whole table)    

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| | | **TRAPRIPC1**| ||
|50| Name |an..35 |D| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  - | C50, NC50
|50|Street and number |an..35 |D| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C50, NC50
|50|Postal code |an..9 |D| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|- | C50, NC50
|50|City |an..35 |D| 22 |NAD[22] \(3035=AF).3164| CitPC124|- | C50, NC50
|50|Country code |a2 |D| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8 | C50, NC50
|50|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |D| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | C111, C236, NR1|
|50|Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904, NR1

(Scroll right to see the whole table)      

**SAD box** | **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNOR) TRADER** | | **O**| | | **TRACONCO1**|- | **R10**
|2| Name |an..35 |R| 22 |NAD[22] \(3035=CZ).C080.3036#1| NamCO17|  -|-
|2| Street and number |an..35 |R| 22 |NAD[22] \(3035=CZ).C059.3042#1| StrAndNumCO122| -|-
|2| Postal code |an..9 |R| 22 |NAD[22] \(3035=CZ).3251| PosCodCO123|-|-
|2| City |an..35 |R| 22 |NAD[22] \(3035=CZ).3164| CitCO124|-|-
|2| Country code |a2 |R| 22 |NAD[22] \(3035=CZ).3207 |CouCO125|8 | -
|2| NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CZ).3229| NADLNGCO |12 | TR99
|2| EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CZ).C082.3039 |TINCO159|- |-

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNEE) TRADER** | | **D**| | | **TRACONCE1**|- | **R11, C1**
|8|Name |an..35 |R| 22 |NAD[22] \(3035=CN).C080.3036#1| NamCE17|  -|-
|8|Street and number |an..35 |R| 22 |NAD[22] \(3035=CN).C059.3042#1| StrAndNumCE122| -|-
|8|Postal code |an..9 |R| 22 |NAD[22] \(3035=CN).3251| PosCodCE123|-|-
|8|City |an..35 |R| 22 |NAD[22] \(3035=CN).3164| CitCE124|-|-
|8|Country code |a2 |R| 22 |NAD[22] \(3035=CN).3207 |CouCE125| 8 | -
|8|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CN).3229| NADLNGCE |12 | TR99
|8|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CN).C082.3039 |TINCE159|-|-

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(AUTHORISED CONSIGNEE) TRADER** | | **O**|  | | **TRAAUTCONTRA**|- | **R15**
||EORI-TIN (Turn) |an..17 |R| 22 |NAD[22] \(3035=TD).C082.3039 |TINTRA59|-|-


(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(DEPARTURE) CUSTOMS OFFICE** | | **R**|-- | | **CUSOFFDEPEPT**| -|-
|C|Reference number |an8 |R| 4 |LOC[4] \(3227=118).C517.3225|RefNumEPT1|- | R901

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(TRANSIT) CUSTOMS OFFICE occurs 9** | | **D**| **-** | | **CUSOFFTRARNS**|- | C30, R902
|51|Reference number |an8 |R| 4 |LOC[4] \(3227=50).C517.3225|RefNumRNS1|- | R906, R907, R908, R910
||Arrival Time |n12 |D| 4 |LOC[4] \(3227=50).C519.3223|ArrTimTRACUS085|- | C598, R660

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DESTINATION) CUSTOMS OFFICE** | | **R**| **-** | | **CUSOFFDESEST**| | |
|53| Reference number |an8 |R| 4 |LOC[4] \(3227=45).C517.3225|RefNumEST1|- | R901, R904, R905

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **CONTROL RESULT** | | **O**| **-** | | **CONRESERS**|- | **R160**
|D| Control result code |an2 |R| 11 |FTX[11] \(4451=ADO).C107.4441|ConResCodERS16|47 | R903
|D| Date limit|n8 |R| 5 |DTM[5] \(C507.2005=268).C507.2380|DatLimERS69|-|-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **REPRESENTATIVE** | | **O**| **-** | | **REPREP**| -|-
|50| Name|an..35 |R| 22 |NAD[22] \(3035=AH).C080.3036#1|NamREP5|-|-
|50| Representative capacity|an..35 |O| 11 |FTX[11] \(4451=ACP).C108.4440#1|RepCapREP18|-|-
|| Representative capacity LNG |a2 |O| 11 |FTX[11] \(4451=ACP).3453|RepCapREP18LNG |12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **SEALS INFO** | | **O**| **-** | | **SEAINFSLIType**|- | **R165**
|D|Seals number|n..4 |R| 145 |CNT[145] \(C270.6069=16).C270.6066|SeaNumSLI2|-|-
||**SEALS ID occurs 99**|| **R**| **-** || **SEAIDSID**|-|-
|D|SEALS ID Seals identity|an..20 |R| 10 |SEL[10] \(9308=0).C215.9302|SeaIdeSID1|-|-
|| SEALS ID Seals identity LNG|a2 |O| 10 |SEL[10] \(9308=0).4517|SeaIdeSID1LNG|12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **GUARANTEE occurs 9**|| **R**| **-** || **GUAGUA**|-|-
|52| Guarantee type |an1 |R| 12 |RFF[12] \(C506.1153=ABL).C506.1154|GuaTypGUA1|51 | C900
|| **GUARANTEE REFERENCE occurs 99**|| **D**| **-** || **GUAREFREF**|- | **C085**
|52|GUARANTEE REFERENCE Guarantee reference number (GRN) |an..24 |D| 14 |RFF(C506.1153=ABL).PAC[14] \(7224=1).C402.7064#1|GuaRefNumGRNREF1|- | C125, TR301
|52|GUARANTEE REFERENCE Other guarantee reference |an..35 |D| 14 |RFF(C506.1153=ABL).PAC[14]\(7224=1).C402.7064#2|OthGuaRefREF4|- | C130, R900
|52| GUARANTEE REFERENCE Access code |an4 |D| 14 |RFF(C506.1153=ABL).PAC[14] \(7224=1).C402.7077|AccCodREF6|- | C86
|| **GUARANTEE REFERENCE - VALIDITY LIMITATION EC**|| **O**| **-** || **VALLIMECVLE**|-|-
|52| GUARANTEE REFERENCE - VALIDITY LIMITATION EC. Not valid for EC|n1 |R| 15 |RFF(C506.1153=ABL).PAC(7224=1).PCI[15] \(4233=19).C210.7102#1| NotValForECVLE1 |27 | R230
|| **GUARANTEE REFERENCE - VALIDITY LIMITATION NON EC occurs 99**|| **O**| **-** || **VALLIMNONECLIM**|-|-
|52| GUARANTEE REFERENCE - VALIDITY LIMITATION NON EC. Not valid for other contracting parties |a2 |R| 15 |RFF(C506.1153=ABL).PAC(7224=1).PCI[15] \(4233=28).C210.7102#1| NotValForOthConPLIM2 |71 | R231

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **GOODS ITEM occurs 999**|| **R**| **-** || **GOOITEGDS**|-|-
|32|Item number |n..5 |R| 92 |CST[92].1496 | IteNumGDS7 | - | R5, R7, TR1200
|33|Commodity code (taric code) |an..22 |D| 92 |CST[92].C246#1.7361 | ComCodTarCodGDS10 | - | C15, R60, R470
|1|Type of declaration |an..9 |D| 92 |CST[92].C246#5.7361 | DecTypGDS15 | 31 | C45
|31| Goods description |an..260 |R| 93 |CST.FTX[93] \(4451=AAA).C108.4440#1 | GooDesGDS23 | -|-
||Goods description LNG |a2 |O| 93 |CST.FTX[93] \(4451=AAA).3453 | GooDesGDS23LNG | 12 | TR99
|35|Gross mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAB)(C174.6411=KGM).C174.6314| GroMasGDS46 | - | R700
|38| Net mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAA)(C174.6411=KGM).C174.6314 | NetMasGDS48 | -|-
|15A| Country of dispatch/export code |a2 |D| 94 |CST.LOC[94] \(3227=35).C517.3225 | CouOfDisGDS58 | 8 | C135
|17A|Country of destination code |a2 |D| 94 |CST.LOC[94] \(3227=36).C517.3225| CouOfDesGDS59 | 8 | C140
||Transport charges/ Method of Payment |a1 |D| 98 |CST.TDT[98] \(8051=10).C228.8179| MetOfPayGDI12 | 116 | C186, C576, TR9120
||Commercial Reference Number|an..70 |D| 93 |CST.FTX[93] \(4451=IND).C108.4440#1| ComRefNumGIM1 | - | C186, C547, R876
||UN dangerous goods code|an4 |O| 98 |CST.TDT[98] \(8051=10).C222.8213| UNDanGooCodGDI1 | 101 | C186
|| **PREV ADMIN REF occurs 9**|| **D**| **-** || **PREADMREFAR2**|- | **C35**
|40|PREV ADMIN REF Previous document type|an..6 |R| 111 |CST.DOC[111] \(C002.1001=190).C002.1000| PreDocTypAR21 | - | R20, TR100
|40|PREV ADMIN REF Previous document reference|an..35 |R| 111 |CST.DOC[111] \(C002.1001=190).C503.1004| PreDocRefAR26 | -|-
||PREV ADMIN REF Previous document reference LNG|a2 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.3453| PreDocRefLNG | 12 | TR99
|40| PREV ADMIN REF Complement of information |an..26 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.1366| ComOfInfAR29| -|-
||PREV ADMIN REF Complement of information LNG |a2 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.1373| ComOfInfAR29LNG| 12 | TR99
||**PRODUCED DOC/CERT occurs 99**|| **D**| **-** || **PRODOCDC2** |- | **C903, C547**
|44|PRODUCED DOC/CERT Document type|an..4 |R| 111 |CST.DOC[111] \(C002.1001=916).C002.1000| DocTypDC21 | 13 | C901, TR0103
|44|PRODUCED DOC/CERT Document reference|an..35|D| 111 |CST.DOC[111] \(C002.1001=916).C503.1004| DocRefDC23 | - | C902
||PRODUCED DOC/CERT Document reference LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.3453| DocRefDCLNG | 12 | TR99
|44|PRODUCED DOC/CERT Complement of information|an..26|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1366| ComOfInfDC25 | -|-
||PRODUCED DOC/CERT Complement of information LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1373| ComOfInfDC25LNG |12 | TR99
|| **SPECIAL MENTIONS occurs 99**|| **O**| **-** || **SPEMENMT2** |- | **R027**
|44|SPECIAL MENTIONS Additional information|an..70|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).C108.4440#1| AddInfMT21 | -|-
||SPECIAL MENTIONS Additional information LNG|a2|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).3453| AddInfMT21LNG | 12 | TR99
|44|SPECIAL MENTIONS Additional information coded|an..5|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).C107.4441| AddInfCodMT23 | 39 | TR101
|44|SPECIAL MENTIONS Export from EC|n1|D| 115 |CST.TOD[115] \(4055=2).C100.4053| ExpFroECMT24 | 27 | C75, R75
|44|SPECIAL MENTIONS Export from country|a2|D| 115 |CST.TOD[115] \(4055=2).C100.1131| ExpFroCouMT25 | 63 | C75, R75
|| **(CONSIGNOR) TRADER**|| **O**| **-** || **TRACONCO2** |- | **R10**
|02|(CONSIGNOR) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C080.3036#1| NamCO27 | -|-
|02|(CONSIGNOR) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CZ).3251| PosCodCO223 | -|-
|02|(CONSIGNOR) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CZ).3164| CitCO224 | -|-
|02|(CONSIGNOR) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CZ).3207| CouCO225 | 8 | -
|02|(CONSIGNOR) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CZ).3229| NADLNGGTCO | 12 | TR99
|02|(CONSIGNOR) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CZ).C082.3039| TINCO259 | -|-
||**(CONSIGNEE) TRADER**|| **D**| **-** || **TRACONCE2** |- | **R11, C002**
|08|(CONSIGNEE) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CN).C080.3036#1| NamCE27 | -|-
|08|(CONSIGNEE) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CN).C059.3042#1| StrAndNumCE222| -|-
|08|(CONSIGNEE) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CN).3251| PosCodCE223 | -|-
|08|(CONSIGNEE) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CN).3164| CitCE224 | -|-
|08|(CONSIGNEE) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CN).3207| CouCE225 | 8 | -
|08|(CONSIGNEE) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CN).3229| NADLNGGICE | 12 | TR99
|08|(CONSIGNEE) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CN).C082.3039| TINCE259 | -|-
|| **CONTAINERS occurs 99**|| **D**| **-** || **CONNR2** |- | **C55**
|31|CONTAINERS Container number|an..17|R| 105 |CST.RFF[105] \(C506.1153=AAQ).C506.1154| ConNumNR21 | -|-
|| **PACKAGES occurs 99**|| **R**| **-** || **PACGS2** |-|-
|31|PACKAGES Marks & numbers of packages|an..42|D| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).C210.7102#1| MarNumOfPacGS21 | - | C60
||PACKAGES Marks & numbers of packages LNG|a2|O| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).8275| MarNumOfPacGS21LNG | 12 | TR99
|31|PACKAGES Kind of packages|an..3|R| 99 |CST.PAC[99] \(7224=6).C402.7077| KinOfPacGS23 | 17 | -
|31|PACKAGES Number of packages|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#1| NumOfPacGS24 | - | C60, R021, TR0022
|31|PACKAGES Number of pieces|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#2| NumOfPieGS25| - | C60
||**SGI CODES occurs 9**|| **O**| **-** || **SGICODSD2** |- | **R155**
|31|SGI CODES Sensitive goods code|n..2|O| 131 |CST.GIR[131] \(7297=3).C206#2.7402| SenGooCodSD22| 64 | R156
|31|SGI CODES Sensitive quantity|n..11,3|R| 131 |CST.GIR[131] \(7297=3).C206#1.7402| SenQuaSD23| -|-
||**(CONSIGNOR-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACORSECGOO021** |- | **C186, C187**
||Name|an..35|D| 97 |NAD[97] \(3035=GM).C080.3036#1| NamTRACORSECGOO025 | - | C501
||Street and number|an..35|D| 97 |NAD[97] \(3035=GM).C059.3042#1| StrNumTRACORSECGOO027 | - | C501
||Postal code|an..9|D| 97 |NAD[97] \(3035=GM).3251| PosCodTRACORSECGOO026 | - | C501
||City|an..35|D| 97 |NAD[97] \(3035=GM).3164| CitTRACORSECGOO022 | - | C501
||Country code|a2|D| 97 |NAD[97] \(3035=GM).3207| CouCodTRACORSECGOO023 | 8 | C501
||NAD_LNG|a2|O| 97 |NAD[97] \(3035=GM).3229| TRACORSECGOO021LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 97 |NAD[97] \(3035=GM).C082.3039| TINTRACORSECGOO028 | - | C572
||**(CONSIGNEE-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACONSECGOO013** |- | **C186, C188**
||Name|an..35|D| 97 |NAD[97] \(3035=DP).C080.3036#1| NamTRACONSECGOO017 | - | C501
||Street and number|an..35|D| 97 |NAD[97] \(3035=DP).C059.3042#1| StrNumTRACONSECGOO019 | - | C501
||Postal code|an..9|D| 97 |NAD[97] \(3035=DP).3251| PosCodTRACONSECGOO018 | - | C501
||City|an..35|D| 97 |NAD[97] \(3035=DP).3164| CityTRACONSECGOO014 | - | C501
||Country code|a2|D| 97 |NAD[97] \(3035=DP).3207| CouCodTRACONSECGOO015 | 8 | C501
||NAD_LNG|a2|O| 97 |NAD[97] \(3035=DP).3229| TRACONSECGOO013LNG | 12 | TR99
||EORI-TIN (Turn)|an..17|O| 97 |NAD[97] \(3035=DP).C082.3039| TINTRACONSECGOO020 | - | C596


(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **ITINERARY occurs 99**|| **D**| **-** || **ITI** |- | **C186, C587**
|| Country of routing code|a2|R| 9 |EQD[9] \(8053=CH).C237.3207| CouOfRouCodITI1 | 8 | -

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CARRIER) TRADER occurs 1**|| **D**| **-** || **CARTRA100** |- | **C186, R181**
|| Name|an..35|D| 22 |NAD[22] \(3035=GA).C080.3036#1| NamCARTRA121 | - | C501
|| Street and number|an..35|D| 22 |NAD[22] \(3035=GA).C059.3042#1| StrAndNumCARTRA254 | - | C501
|| Postal code|an..9|D| 22 |NAD[22] \(3035=GA).3251 | PosCodCARTRA121 | - | C501
|| City|an..35|D| 22 |NAD[22] \(3035=GA).3164| CitCARTRA789 | - | C501
|| Country code|a2|D| 22 |NAD[22] \(3035=GA).3207| CouCodCARTRA587 | 8 | C501
|| NAD_LNG|a2|O| 22 |NAD[22] \(3035=GA).3229| NADCARTRA121 | 12 | TR99
|| EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=GA).C082.3039| TINCARTRA254 | -|-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(CONSIGNOR-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACORSEC037** |- | **C186, C187**
||Name|an..35|D| 22 |NAD[22] \(3035=GL).C080.3036#1| NamTRACORSEC041 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=GL).C059.3042#1| StrNumTRACORSEC043 | - | C501
||Postal code|an..9|D| 22 |NAD[22] \(3035=GL).3251 | PosCodTRACORSEC042 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=GL).3164| CitTRACORSEC038 | - | C501
||Country code|a2|D| 22 |NAD[22] \(3035=GL).3207| CouCodTRACORSEC039| 8 | C501
||NAD_LNG|a2|O| 22 |AD[22] \(3035=GL).3229| TRACORSEC037LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |AD[22] \(3035=GL).C082.3039| TINTRACORSEC044 | - | C572


(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNEE-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACONSEC029** |- | **C186, C188**
||Name|an..35|D| 22 |NAD[22] \(3035=UC).C080.3036#1| NameTRACONSEC033 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=UC).C059.3042#1| StrNumTRACONSEC035 | - | C501
||Postal code|an..9|D| 22 |NNAD[22] \(3035=UC).3251| PosCodTRACONSEC034 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=UC).3164| CitTRACONSEC030| - | C501
||Country code|a2|D| 22 |NAD[22] \(3035=UC).3207| CouCodTRACONSEC031| 8 | C501
||NAD_LNG|a2|O| 22 |NAD[22] \(3035=UC).3229| TRACONSEC029LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=UC).C082.3039| TINTRACONSEC036 | - | C596

## Declaration rejected (IE16 - E_DEC_REJ)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | | |
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
|7|Reference number (LRN)|an..22 |R| 12 |RFF[12] \(C506.1153=ABE).C506.1154| RefNumHEA4| -|-
|1|Type of declaration| an..9|R| 2 |BGM[2].C002.1000 |TypOfDecHEA24| 31 | -
||Declaration rejection date| n8 |R| 3 |DTM[3] \(C507.2005=46).C507.2380 |DecRejDatHEA159| -|-
||Declaration rejection reason| an..350 |O| 4 |FTX[4] \(4451=ACD).C108.4440#1 |DecRejReaHEA252| -|-
||Declaration rejection reason LNG| a2 |O| 4 |FTX[4] \(4451=ACD).3453 |DecRejReaHEA252LNG| 12 | TR99


(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **FUNCTIONAL ERROR occurs 999**|| **D**| **-** || **FUNERRER1** |- | **R123**
||Error type| n2|R| 4 |FTX[4] \(4451=AAO).C107.4441|ErrTypER11| 49 | -
||Error pointer| an..210|R| 4 |FTX[4] \(4451=AAO).C108.4440#1|ErrPoiER12| 100 | -
||Error reason| an..6|O| 4 |FTX[4] \(4451=AAO).C108.4440#4|ErrReaER13| -|-
||Original attribute value| an..140|O| 4 |FTX[4] \(4451=AAP).C108.4440#1|OriAttValER14| -|-


## Goods release notification (IE25 - E_GDS_REL)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
|| Document/reference number (MRN)|an..21 |R| 2 |BGM[2] \(1225=11).C106.1004 | DocNumHEA5| -|-
|| Goods release date | n8|D| 3 |DTM[3] \(C507.2005=261).C507.2380| GooRelDatHEA176|  -|-


(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DESTINATION) TRADER**|| **R**| **-** || **TRADESTRD** |-|-
||Name|an..35|D| 9 |NAD[9] \(3035=CPD).C080.3036#1| NamTRD7 | - | C501
||Street and number|an..35|D| 9 |NAD[9] \(3035=CPD).C059.3042#1| StrAndNumTRD22 | - | C160
||Postal code|an..9|D| 9 |NAD[9] \(3035=CPD).3251| PosCodTRD23 | - | C160
||City|an..35|D| 9 |NAD[9] \(3035=CPD).3164| CitTRD24| - | C160
||Country code|a2|D| 9 |NAD[9] \(3035=CPD).3207| CouTRD25| 8 | C160
||NAD_LNG|a2|O| 9 |NAD[9] \(3035=CPD).3229| NADLNGRD | 12 | TR99
||EORI-TIN (Turn)|an..17|O| 9 |NAD[9] \(3035=CPD).C082.3039| TINTRD59 | - | R012

(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRESENTATION OFFICE) CUSTOMS OFFICE**|| **R**| **-** || **CUSOFFPREOFFRES** |-|-
||Reference number| an8 |R| 6 |LOC[6] \(3227=22).C517.3225 | RefNumRES1| - |-


## Movement Reference Number (MRN) allocated (IE28 - E_MRN_ALL)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | ||
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
|7|Reference number (LRN)|an..22 |R| 12 |RFF[12] \(C506.1153=ABE).C506.1154| RefNumHEA4| -|-
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2] \(1225=11).C106.1004 | DocNumHEA5| -|-
||Acceptance date | n8|R| 3 |DTM[3] \(C507.2005=148).C507.2380| AccDatHEA158|  -|-


(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| | | **TRAPRIPC1**| ||
|50| Name |an..35 |D| 9 |NAD[9] \(3035=AF).C080.3036#1| NamPC17|  - | C160
|50|Street and number |an..35 |D| 9 |NAD[9] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C160
|50|Postal code |an..9 |D| 9 |NAD[9] \(3035=AF).3251| PosCodPC123|- | C160
|50|City |an..35 |D| 9 |NAD[9] \(3035=AF).3164| CitPC124|- | C160
|50|Country code |a2 |D| 9 |NAD[9] \(3035=AF).3207 |CouPC125|8| C160
|50|NAD_LNG |a2 |O| 9 |NAD[9] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |O| 9 |NAD[9] \(3035=AF).C082.3039 |TINPC159|- | R012|
|50|Holder ID TIR |an..17 |D| 9 |NAD[9] \(3035=AF).C080.3036#2 |HITPC126|- | C904

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(DEPARTURE) CUSTOMS OFFICE** | | **R**|-- | | **CUSOFFDEPEPT**| |-|-
|| Reference number |an8 |R| 6 |LOC[6] \(3227=118).C517.3225|RefNumEPT1|- | -


## Release for Transit  (IE29 - E_REL_TRA)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |- | **R143**
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
|7| Reference number (LRN)|an..22 |R| 12 |RFF[12] \(C506.1153=ABE).C506.1154| RefNumHEA4| -|-
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| -|-
|1|Type of declaration | an..9|R| 2 |BGM[2].C002.1000| TypOfDecHEA24|  31 | R909, R911
|17A|Country of destination code|a2 |D| 4|LOC[4] \(3227=36).C517.3225|CouOfDesCodHEA30 | 8 | C140
|30|Agreed location of goods, code|an..17 |D| 4|LOC[4] \(3227=14).C517.3225|AgrLocOfGooCodHEA38 | - | C100, R41
|30|Agreed location of goods|an..35 |D| 4|LOC[4] \(3227=14).C517.3224|AgrLocOfGooHEA39 | - | C100, R41
||Agreed location of goods LNG|a2 |0| 4|LOC[4] \(3227=14).5479|AgrLocOfGooHEA39LNG | 12 | TR99
|30|Authorised location of goods, code|an..17 |D| 4|LOC[4] \(3227=14).C519.3223|AutLocOfGooCodHEA41 | - | C100, R41
|27|Place of loading, code|an..17 |D| 4|LOC[4] \(3227=9).C517.3225|PlaOfLoaCodHEA46 | - | C191
|15A|Country of dispatch/export code|a2 |D| 4|LOC[4] \(3227=35).C517.3225|CouOfDisCodHEA55 | 8 | C135
||Customs sub place|an..17 |D| 4|LOC[4] \(3227=26).C517.3225|CusSubPlaHEA66 | - | C100, R41
|26|Inland transport mode|n..2 |O| 17|TDT[17] \(8051=1).C220.8067| InlTraModHEA75 | 18 | -
|25|Transport mode at border|n..2 |D| 17|TDT[17] \(8051=11).C220.8067| TraModAtBorHEA76 | 18 | C599
|18|Identity of means of transport at departure (exp/trans)|an..27 |D|17 |TDT[17] \(8051=12).C222.8212| IdeOfMeaOfTraAtDHEA78 | - | TR0035, TR9090
||Identity of means of transport at departure LNG|a2 |O|18 |TDT(8051=12).TPL[18].C222.8453| IdeOfMeaOfTraAtDHEA78LNG | 12 | TR99
|18|Nationality of means of transport at departure|a2 |D|17 |TDT[17] \(8051=12).C222.8453| NatOfMeaOfTraAtDHEA80 | 8 | TR0035, TR9095
|21|Identity of means of transport crossing border|an..27 |D|17 |TDT[17] \(8051=11).C222.8212| IdeOfMeaOfTraCroHEA85 | - | C011
||Identity of means of transport crossing border LNG|a2 |O|18 |TDT(8051=11).TPL[18].C222.8453| IdeOfMeaOfTraCroHEA85LNG |12 | TR99
|21| Nationality of means of transport at crossing border|n..2 |D|17 |TDT[17] \(8051=11).C222.8453| NatOfMeaOfTraCroHEA87 | 8 | R36, C10
||Type of means of transport crossing border|n..2 |O|17 |TDT[17] \(8051=11).C228.8179| TypOfMeaOfTraCroHEA88 |18 | -
|19|Containerised indicator|n1 |R|6 |GIS[6] \(C529.1131=109).C529.7365| ConIndHEA96 |27 | R230
||NCTS return copy|n1 |R|6 |GIS[6] \(C529.1131=62).C529.7365| NCTRetCopHEA104 |27 | R330
||Acceptance date|n8 |R|5 |DTM[5] \(C507.2005=148).C507.2380| AccDatHEA158|-|-
||Issuing date|n8 |R|5 |DTM[5] \(C507.2005=182).C507.2380| IssDatHEA186|-|-
||Dialog language indicator at departure | a2 |O| 11 |FTX[11] \(4451=ACB).3453| DiaLanIndAtDepHEA254| 12 | R100
||NCTS accompanying document language code|a2 |R|11 |FTX[11] \(4451=ALL).3453| NCTSAccDocHEA601LNG |12 | -
|5|Total number of items|n..5 |R|145 |CNT[145] \(C270.6069=5).C270.6066| TotNumOfIteHEA305 | -|-
|6|Total number of packages|n..7 |O|145 |CNT[145] \(C270.6069=11).C270.6066| TotNumOfPacHEA306 | - | R105
|35|Total gross mass|n..11,3 |R|8 |MEA[8] \(6311=WT)(C502.6313=AAD)(C174.6411=KGM).C174.6314| TotGroMasHEA307 | -|-
|D|Binding itinerary|n1 |R|11 |FTX[11] \(4451=ABL).C108.4440#1| BinItiHEA246 | 27 | R230
||Authorisation ID|an..17 |O|12 |RFF[12] \(C506.1153=LAN).C506.1154 | AutIdHEA380| -|-
|50|Declaration date|n8 |R|5 |DTM[5] \(C507.2005=137).C507.2380| DecDatHEA383 | -|-
|50|Declaration place|an..35 |R|4 |LOC[4] \(3227=91).C517.3224| DecPlaHEA394 | -|-
||Declaration place LNG|a2 |O|4 |LOC[4] \(3227=91).5479| DecPlaHEA394LNG | 12 | TR99
||Specific Circumstance Indicator|a1 |D|12 |RFF[12] \(C506.1153=AMJ).C506.1154| SpeCirIndHEA1 | 96 | C186, C825
||Transport charges/ method of payment|a1 |D|11 |FTX[11] \(4451=PAI).4453| TraChaMetOfPayHEA1 | 116 | C186
||Commercial reference number|an..70 |D|7 |FII[7] \(3035=XX).C088.3436| ComRefNumHEA | - | C186, C547, R876
||Security|n1 |O|6 |GIS[6] \(C529.1131=187).C529.7365| SecHEA358 | 117 | R229
||Conveyance reference number|an..35 |O|11 |FTX[11] \(4451=ACR).C108.4440#1| ConRefNumHEA | - | C531
||Place of unloading, code|an..35 |D|4 |LOC[4] \(3227=58).C517.3224| CodPlUnHEA357 | - | C186, C589
||Place of unloading, LNG|a2 |O|4 |LOC[4] \(3227=58).C517.3225| CodPlUnHEA357LNG | 12 | TR0099

(Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| | | **TRAPRIPC1**| ||
|50|Name |an..35 |D| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  - | C50, NC50
|50|Street and number |an..35 |D| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C50, NC50
|50|Postal code |an..9 |D| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|- | C50, NC50
|50|City |an..35 |D| 22 |NAD[22] \(3035=AF).3164| CitPC124|- | C50, NC50
|50|Country code |a2 |D| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8 | C50, NC50
|50|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |D| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | C111, C236, NR1|
|50|Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904, NR1

(Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNOR) TRADER** | | **O**| | | **TRACONCO1**| |- | **R10**
|2|Name |an..35 |R| 22 |NAD[22] \(3035=CZ).C080.3036#1| NamCO17|  -|-
|2|Street and number |an..35 |R| 22 |NAD[22] \(3035=CZ).C059.3042#1| StrAndNumCO122| -|-
|2|Postal code |an..9 |R| 22 |NAD[22] \(3035=CZ).3251| PosCodCO123|-|-
|2|City |an..35 |R| 22 |NAD[22] \(3035=CZ).3164| CitCO124|-|-
|2|Country code |a2 |R| 22 |NAD[22] \(3035=CZ).3207 |CouCO125|8 | -
|2|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CZ).3229| NADLNGCO |12 | TR99
|2|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CZ).C082.3039 |TINCO159|- |-

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNEE) TRADER** | | **D**| | | **TRACONCE1**| |- | **R11, C1**
|8|Name |an..35 |R| 22 |NAD[22] \(3035=CN).C080.3036#1| NamCE17|  -|-
|8|Street and number |an..35 |R| 22 |NAD[22] \(3035=CN).C059.3042#1| StrAndNumCE122| -|-
|8|Postal code |an..9 |R| 22 |NAD[22] \(3035=CN).3251| PosCodCE123|-|-
|8|City |an..35 |R| 22 |NAD[22] \(3035=CN).3164| CitCE124|-|-
|8|Country code |a2 |R| 22 |NAD[22] \(3035=CN).3207 |CouCE125| 8 | -
|8|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CN).3229| NADLNGCE |12 | TR99
|8|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CN).C082.3039 |TINCE159|-|-

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(AUTHORISED CONSIGNEE) TRADER** | | **O**|  | | **TRAAUTCONTRA**|- | **R15**
||EORI-TIN (Turn) |an..17 |R| 22 |NAD[22] \(3035=TD).C082.3039 |TINTRA59|- |-


(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DEPARTURE) CUSTOMS OFFICE** | | **R**|-- | | **CUSOFFDEPEPT**| |-|-
|C|Reference number |an8 |R| 4 |LOC[4] \(3227=118).C517.3225|RefNumEPT1|- | C901

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(TRANSIT) CUSTOMS OFFICE occurs 9** | | **D**| **-** | | **CUSOFFTRARNS**| - | **C30, R902**
|51|Reference number |an8 |R| 4 |LOC[4] \(3227=50).C517.3225|RefNumRNS1|- | R906, R907, R908, R910
||Arrival Time |n12 |D| 4 |LOC[4] \(3227=50).C519.3223|ArrTimTRACUS085|- |C598, R660

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DESTINATION) CUSTOMS OFFICE** | | **R**| **-** | | **CUSOFFDESEST**| ||
|53| Reference number |an8 |R| 4 |LOC[4] \(3227=45).C517.3225|RefNumEST1|- | R901, R904, R905

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(RETURN COPIES) CUSTOMS OFFICE** | | **O**| **-** | | **CUSOFFRETCOPOCP**|- | **R330**
||Reference number |an8 |R| 4 |LOC[4] \(3227=168).C517.3225| RefNumOCP1|  -|-
||Customs office name |an..35 |R| 4 |LOC[4] \(3227=168).C517.3224| CusOffNamOCP2|  -|-
||Street and number |an..35 |R| 4 |LOC[4] \(3227=168).C519.3222| StrAndNumOCP3| -|-
||Country code |a2 |R| 4 |LOC[4] \(3227=168).C519.3223 |CouOCP4| 9 | -
||Postal code |an..9 |R| 4 |LOC[4] \(3227=168).C553.3233| PosCodOCP6|-|-
||City |an..35 |R| 4 |LOC[4] \(3227=168).C553.3232| CitOCP7|-|-
||NAD_LNG |a2 |O| 4 |LOC[4] \(3227=168).5479| NADLNGOCP |12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **CONTROL RESULT** | | **O**| **-** | | **CONRESERS**|- | **R335**
|D|Control date |n8 |R| 5 |DTM[5] \(C507.2005=9).C507.2380|ConDatERS14|-|-
|D|Control result code |an2 |R| 11 |FTX[11] \(4451=ADO).C107.4441|ConResCodERS16|47 | R903
|D|Controlled by|an..35|R| 22 |NAD[22] \(3035=EI).C082.3039|ConByERS18|-|-
||Controlled by LNG|a2|O| 22 |NAD[22] \(3035=EI).3207|ConByERS18LNG |12 | TR99
|D|Date limit|n8 |R| 5 |DTM[5] \(C507.2005=268).C507.2380|DatLimERS69|-|-

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **REPRESENTATIVE** | | **O**| **-** | | **REPREP**| |-
|50|Name|an..35 |R| 22 |NAD[22] \(3035=AH).C080.3036#1|NamREP5|-|-
|50| Representative capacity|an..35 |O| 11 |FTX[11] \(4451=ACP).C108.4440#1|RepCapREP18|-|-
||Representative capacity LNG |a2 |O| 11 |FTX[11] \(4451=ACP).3453|RepCapREP18LNG |12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **SEALS INFO** | | **O**| **-** | | **SEAINFSLI**|- | **R165**
|D|Seals number|n..4 |R| 145 |CNT[145] \(C270.6069=16).C270.6066|SeaNumSLI2|-|-
|| **SEALS ID occurs 99**|| **R**| **-** || **SEAIDSID**|-|-
|D|SEALS ID Seals identity|an..20 |R| 10 |SEL[10] \(9308=0).C215.9302|SeaIdeSID1|-|-
||SEALS ID Seals identity LNG|a2 |O| 10 |SEL[10] \(9308=0).4517|SeaIdeSID1LNG|12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**GUARANTEE occurs 9**|| **R**| **-** || **GUAGUA**|-|-
|52|Guarantee type |an1 |R| 12 |RFF[12] \(C506.1153=ABL).C506.1154|GuaTypGUA1|51 | C900
|| **GUARANTEE REFERENCE occurs 99**|| **D**| **-** || **GUAREFREF**|- | **C085**
|52|GUARANTEE REFERENCE Guarantee reference number (GRN) |an..24 |D| 14 |RFF(C506.1153=ABL).PAC[14] \(7224=1).C402.7064#1|GuaRefNumGRNREF1|- | C125, TR301
|52|GUARANTEE REFERENCE Other guarantee reference |an..35 |D| 14 |RFF(C506.1153=ABL).PAC[14]\(7224=1).C402.7064#2|OthGuaRefREF4|- | C130, R900
|52|GUARANTEE REFERENCE Access code |an4 |D| 14 |RFF(C506.1153=ABL).PAC[14] \(7224=1).C402.7077|AccCodREF6|- | C86
||**GUARANTEE REFERENCE - VALIDITY LIMITATION EC**|| **O**| **-** || **VALLIMECVLE**|-|-
|52|GUARANTEE REFERENCE - VALIDITY LIMITATION EC. Not valid for EC|n1 |R| 15 |RFF(C506.1153=ABL).PAC(7224=1).PCI[15] \(4233=19).C210.7102#1| NotValForECVLE1 |27 | R230
|| **GUARANTEE REFERENCE - VALIDITY LIMITATION NON EC occurs 99**|| **O**| **-** || **VALLIMNONECLIM**|-|-
|52| GUARANTEE REFERENCE - VALIDITY LIMITATION NON EC. Not valid for other contracting parties |a2 |R| 15 |RFF(C506.1153=ABL).PAC(7224=1).PCI[15] \(4233=28).C210.7102#1| NotValForOthConPLIM2 |71 | R231

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**GOODS ITEM occurs 999**|| **R**| **-** || **GOOITEGDS**|-|-
|32|Item number |n..5 |R| 92 |CST[92].1496 | IteNumGDS7 | - | R5, R7, TR1200
|33| Commodity code (taric code) |an..22 |D| 92 |CST[92].C246#1.7361 | ComCodTarCodGDS10 | - | C15, R60, R470
|1| Type of declaration |an..9 |D| 92 |CST[92].C246#5.7361 | DecTypGDS15 | 31 | C45
31|Goods description |an..260 |R| 93 |CST.FTX[93] \(4451=AAA).C108.4440#1 | GooDesGDS23 | -|-
||Goods description LNG |a2 |O| 93 |CST.FTX[93] \(4451=AAA).3453 | GooDesGDS23LNG | 12 | TR99
|35|Gross mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAB)(C174.6411=KGM).C174.6314| GroMasGDS46 | - | R700
|38|Net mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAA)(C174.6411=KGM).C174.6314 | NetMasGDS48 | -
|15A|Country of dispatch/export code |a2 |D| 94 |CST.LOC[94] \(3227=35).C517.3225 | CouOfDisGDS58 | 8 | C135
|17A|Country of destination code |a2 |D| 94 |CST.LOC[94] \(3227=36).C517.3225| CouOfDesGDS59 | 8 | C140
||Transport charges/ Method of Payment |a1 |D| 98 |CST.TDT[98] \(8051=10).C228.8179| MetOfPayGDI12 | 116 | C186, C576, TR9120
||Commercial Reference Number|an..70 |D| 93 |CST.FTX[93] \(4451=IND).C108.4440#1| ComRefNumGIM1 | - | C186, C547, R876
||UN dangerous goods code|an4 |O| 98 |CST.TDT[98] \(8051=10).C222.8213| UNDanGooCodGDI1 | 101 | C186
|| **PREV ADMIN REF occurs 9**|| **D**| **-** || **PREADMREFAR2** |- | **C35**
|40|PREV ADMIN REF Previous document type|an..6 |R| 111 |CST.DOC[111] \(C002.1001=190).C002.1000| PreDocTypAR21 | - | R020, TR100
|40|PREV ADMIN REF Previous document reference|an..35 |R| 111 |CST.DOC[111] \(C002.1001=190).C503.1004| PreDocRefAR26 | -|-
||PREV ADMIN REF Previous document reference LNG|a2 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.3453| PreDocRefLNG | 12 | TR99
|40|PREV ADMIN REF Complement of information |an..26 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.1366| ComOfInfAR29| -|-
||PREV ADMIN REF Complement of information LNG |a2 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.1373| ComOfInfAR29LNG| 12 | TR99
||**PRODUCED DOC/CERT occurs 99**|| **D**| **-** || **PRODOCDC2** |- | **C547, C903**
|44|PRODUCED DOC/CERT Document type|an..4 |R| 111 |CST.DOC[111] \(C002.1001=916).C002.1000| DocTypDC21 | 13 | C901, TR0103
|44|PRODUCED DOC/CERT Document reference|an..35|D| 111 |CST.DOC[111] \(C002.1001=916).C503.1004| DocRefDC23 | - | C902
||PRODUCED DOC/CERT Document reference LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.3453| DocRefDCLNG | 12 | TR99
|44|PRODUCED DOC/CERT Complement of information|an..26|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1366| ComOfInfDC25 | -|-
||PRODUCED DOC/CERT Complement of information LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1373| ComOfInfDC25LNG |12 | TR99
|| **SPECIAL MENTIONS occurs 99**|| **O**| **-** || **SPEMENMT2** |- | **R027**
|44|SPECIAL MENTIONS Additional information|an..70|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).C108.4440#1| AddInfMT21 | -|-
||SPECIAL MENTIONS Additional information LNG|a2|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).3453| AddInfMT21LNG | 12 | TR99
|44|SPECIAL MENTIONS Additional information coded|an..5|O| 117 |CCST.TOD(4055=2).FTX[117] \(4451=ACB).C107.4441| AddInfCodMT23 | - | TR101
|44|SPECIAL MENTIONS Export from EC|n1|D| 115 |CST.TOD[115] \(4055=2).C100.4053| ExpFroECMT24 | 27 | C75, R75
|44|SPECIAL MENTIONS Export from country|a2|D| 115 |CST.TOD[115] \(4055=2).C100.1131| ExpFroCouMT25 | 63 | C75, R75
||**(CONSIGNOR) TRADER**|| **O**| **-** || **TRACONCO2** |- | **R10**
|02|(CONSIGNOR) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C080.3036#1| NamCO27 | -|-
|02|(CONSIGNOR) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C059.3042#1| StrAndNumCO222 | -|-
|02|(CONSIGNOR) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CZ).3251| PosCodCO223 | -|-
|02|(CONSIGNOR) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CZ).3164| CitCO224 | -|-
|02|(CONSIGNOR) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CZ).3207| CouCO225 | 8 | -
|02|(CONSIGNOR) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CZ).3229| NADLNGGTCO | 12 | TR99
|02|(CONSIGNOR) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CZ).C082.3039| TINCO259 | -|-
||**(CONSIGNEE) TRADER**|| **D**| **-** || **TRACONCE2** |- | **R11, C002**
|08|(CONSIGNEE) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CN).C080.3036#1| NamCE27 | -|-
|08|(CONSIGNEE) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CN).C059.3042#1| StrAndNumCE222| -|-
|08|(CONSIGNEE) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CN).3251| PosCodCE223 | -|-
|08|(CONSIGNEE) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CN).3164| CitCE224 | -|-
|08|(CONSIGNEE) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CN).3207| CouCE225 | 8 | -
|08|(CONSIGNEE) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CN).3229| NADLNGGICE | 12 | TR99
|08|(CONSIGNEE) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CN).C082.3039| TINCE259 | -|-
||**CONTAINERS occurs 99**|| **D**| **-** || **CONNR2** |- | **C55**
|31| CONTAINERS Container number|an..17|R| 105 |CST.RFF[105] \(C506.1153=AAQ).C506.1154| ConNumNR21 | -|-
|| **PACKAGES occurs 99**|| **R**| **-** || **PACGS2** |-|-
|31|PACKAGES Marks & numbers of packages|an..42|D| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).C210.7102#1| MarNumOfPacGS21 | - | C60
|| PACKAGES Kind of packages|an..3|R| 99 |CST.PAC[99] \(7224=6).C402.7077| KinOfPacGS23 | 17 | -
|31|PACKAGES Number of packages|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#1| NumOfPacGS24 | - | C60, R021, TR0022
|31|PACKAGES Number of pieces|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#2| NumOfPieGS25| - | C60
|| **SGI CODES occurs 9**|| **O**| **-** || **SGICODSD2** |- | **R155**
|31|SGI CODES Sensitive goods code|n..2|O| 131 |CST.GIR[131] \(7297=3).C206#2.7402| SenGooCodSD22| 64 | R156
|31|SGI CODES Sensitive quantity|n..11,3|R| 131 |CST.GIR[131] \(7297=3).C206#1.7402| SenQuaSD23| -|-
||**(CONSIGNOR-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACORSECGOO021** |- | **C186, C187**
||Name|an..35|D| 97 |NAD[97] \(3035=GM).C080.3036#1| NamTRACORSECGOO025 | - | C501
||Street and number|an..35|D| 97 |NAD[97] \(3035=GM).C059.3042#1| StrNumTRACORSECGOO027 | - | C501
||Postal code|an..9|D| 97 |NAD[97] \(3035=GM).3251| PosCodTRACORSECGOO026 | - | C501
||City|an..35|D| 97 |NAD[97] \(3035=GM).3164| CitTRACORSECGOO022 | - | C501
||Country code|a2|D| 97 |NAD[97] \(3035=GM).3207| CouCodTRACORSECGOO023 | 8 | C501
||NAD_LNG|a2|O| 97 |NAD[97] \(3035=GM).3229| TRACORSECGOO021LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 97 |NAD[97] \(3035=GM).C082.3039| TINTRACORSECGOO028 | - | C572
||**(CONSIGNEE-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACONSECGOO013** |- | **C186, C188**
||Name|an..35|D| 97 |NAD[97] \(3035=DP).C080.3036#1| NamTRACONSECGOO017 | - | C501
||Street and number|an..35|D| 97 |NAD[97] \(3035=DP).C059.3042#1| StrNumTRACONSECGOO019 | - | C501
||Postal code|an..9|D| 97 |NAD[97] \(3035=DP).3251| PosCodTRACONSECGOO018 | - | C501
||City|an..35|D| 97 |NAD[97] \(3035=DP).3164| CityTRACONSECGOO014 | - | C501
||Country code|a2|D| 97 |NAD[97] \(3035=DP).3207| CouCodTRACONSECGOO015 | 8 | C501
||NAD_LNG|a2|O| 97 |NAD[97] \(3035=DP).3229| TRACONSECGOO013LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 97 |NAD[97] \(3035=DP).C082.3039| TINTRACONSECGOO020 | - | C596

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **ITINERARY occurs 99**|| **D**| **-** || **ITI** |- | **C186, C587**
|| Country of routing code|a2|R| 9 |EQD[9] \(8053=CH).C237.3207| CouOfRouCodITI1 | 8 | -

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
----|---|---|---|---|---|---|---|---
||**(CARRIER) TRADER occurs 1**|| **D**| **-** || **CARTRA100** |- | **C186, R181**
||Name|an..35|D| 22 |NAD[22] \(3035=GA).C080.3036#1| NamCARTRA121 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=GA).C059.3042#1| StrAndNumCARTRA254 | - | C501
||Postal code|an..9|D| 22 |NAD[22] \(3035=GA).3251 | PosCodCARTRA121 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=GA).3164| CitCARTRA789 | - | C501
||Country code|a2|D| 22 |NNAD[22] \(3035=GA).3207| CouCodCARTRA587 | 8 | C501
||NAD_LNG|a2|O| 22 |NAD[22] \(3035=GA).3229| NADCARTRA121 | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=GA).C082.3039| TINCARTRA254 | -|-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(CONSIGNOR-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACORSEC037** |- | **C186, C187**
||Name|an..35|D| 22 |NAD[22] \(3035=GL).C080.3036#1| NameTRACORSEC041 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=GL).C059.3042#1| StrNumTRACORSEC043 | - | C501
||Postal code|an..9|D| 22 |NAD[22] \(3035=GL).3251 | PosCodTRACORSEC042 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=GL).3164| CitTRACORSEC038 | - | C501
||Country code|a2|D| 22 |NAD[22] \(3035=GL).3207| CouCodTRACORSEC039| 8 | C501
||NAD_LNG|a2|O| 22 |NAD[22] \(3035=GL).3229| TRACORSEC037LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=GL).C082.3039| TINTRACORSEC044 | - | C572


(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNEE-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACONSEC029** |- | **C186, C188**
||Name|an..35|D| 22 |NAD[22] \(3035=UC).C080.3036#1| NameTRACONSEC033 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=UC).C059.3042#1| StrNumTRACONSEC035 | - | C501
||Postal code|an..9|D| 22 |NNAD[22] \(3035=UC).3251| PosCodTRACONSEC034 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=UC).3164| CitTRACONSEC030| - | C501
||Country code|a2|D| 22 |NAD[22] \(3035=UC).3207| CouCodTRACONSEC031| 8 | C501
||NAD_LNG|a2|O| 22 |NAD[22] \(3035=UC).3229| TRACONSEC029LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=UC).C082.3039| TINTRACONSEC036 | - | C596

## Unloading permission (IE43 - E_ULD_PER)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |- | **R195** |
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| -|-
||Type of declaration | an..9|D| 2 |BGM[2].C002.1000| TypOfDecHEA24|  31 | -
|17A|Country of destination code|a2 |D| 4|LOC[4] \(3227=36).C517.3225|CouOfDesCodHEA30 | 8 | C140
|15A|Country of dispatch/export code|a2 |D| 4|LOC[4] \(3227=35).C517.3225|CouOfDisCodHEA55 | 8 | C135
|18|Identity of means of transport at departure (exp/trans)|an..27 |D|17 |TDT[17] \(8051=12).C222.8212| IdeOfMeaOfTraAtDHEA78 | - | TR9090
|18|Identity of means of transport at departure LNG|a2 |O|18 |TDT(8051=12).TPL[18].C222.8453| IdeOfMeaOfTraAtDHEA78LNG | 12 | TR99
|18|Nationality of means of transport at departure|a2 |D|17 |TDT[17] \(8051=12).C222.8453| NatOfMeaOfTraAtDHEA80 | 8 | TR0035, TR9095
|19|Containerised indicator|n1 |D|6 |GIS[6] \(C529.1131=109).C529.7365| ConIndHEA96 |27 | R230
||Acceptance date|n8 |D|5 |DTM[5] \(C507.2005=148).C507.2380| AccDatHEA158|-|-
|5|Total number of items|n..5 |D|145 |CNT[145] \(C270.6069=5).C270.6066| TotNumOfIteHEA305 | -|-
|6|Total number of packages|n..7 |O|145 |CNT[145] \(C270.6069=11).C270.6066| TotNumOfPacHEA306 | -|-
|35|Total gross mass|n..11, 3  |D|8 |MEA[8] \(6311=WT)(C502.6313=AAD)(C174.6411=KGM).C174.6314| TotGroMasHEA307 | -|-

(Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(PRINCIPAL) TRADER** | | **D**| | | **TRAPRIPC1**| ||
|50|Name |an..35 |R| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  -|-
|50|Street and number |an..35 |R| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| -|-
|50|Postal code |an..9 |R| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|-|-
|50|City |an..35 |R| 22 |NAD[22] \(3035=AF).3164| CitPC124|-|-
|50|Country code |a2 |R| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8|-
|50|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | R012
|50|Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNOR) TRADER** | | **O**| | | **TRACONCO1**| - | **R10**
|2|Name |an..35 |R| 22 |NAD[22] \(3035=CZ).C080.3036#1| NamCO17|  -|-
|2|Postal code |an..9 |R| 22 |NAD[22] \(3035=CZ).3251| PosCodCO123|-|-
|2|City |an..35 |R| 22 |NAD[22] \(3035=CZ).3164| CitCO124|-|-
|2|Country code |a2 |R| 22 |NAD[22] \(3035=CZ).3207 |CouCO125|8 | -
|2|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CZ).3229| NADLNGCO |12 | TR99
|2|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CZ).C082.3039 |TINCO159|- | R012|

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNEE) TRADER** | | **D**| | | **TRACONCE1**| - | **R11, C1**
|8|Name |an..35 |R| 22 |NAD[22] \(3035=CN).C080.3036#1| NamCE17|  -|-
|8|Street and number |an..35 |R| 22 |NAD[22] \(3035=CN).C059.3042#1| StrAndNumCE122| -|-
|8|Postal code |an..9 |R| 22 |NAD[22] \(3035=CN).3251| PosCodCE123|-|-
|8|City |an..35 |R| 22 |NAD[22] \(3035=CN).3164| CitCE124|-|-
|8|Country code |a2 |R| 22 |NAD[22] \(3035=CN).3207 |CouCE125| 8 | -
|8|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CN).3229| NADLNGCE |12 | TR99
|8|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CN).C082.3039 |TINCE159|- | R012

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(DESTINATION) TRADER** | | **R**| -- | | **TRADESTRD**| ||
||Name |an..35 |D| 22 |NAD[22] \(3035=CPD).C080.3036#1| NamTRD7|  - | C160
||Street and number |an..35 |D| 22 |NAD[22] \(3035=CPD).C059.3042#1| StrAndNumTRD22| - | C160
||Postal code |an..9 |D| 22 |NAD[22] \(3035=CPD).3251| PosCodTRD23|- | C160
||City |an..35 |D| 22 |NAD[22] \(3035=CPD).3164| CitTRD24|- | C160
||Country code |a2 |D| 22 |NAD[22] \(3035=CPD).3207 |CouTRD25| 8 | C160
||NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CPD).3229 |NADLNGRD|12 | TR99
||EORI-TIN (Turn) |an..17 |O| 22 |NAD[22]\(3035=CPD)C082.3039|TINTRD59 | - | R012|

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| ||
||Reference number |an8 |R| 4 |LOC[4] \(3227=118).C517.3225 |RefNumEPT1|- |-|

(Scroll right to see the whole table)     

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(PRESENTATION OFFICE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFPREOFFRES**| ||
||Reference number |an8 |R| 4 |LOC[4] \(3227=22).C517.3225|RefNumRES1|-|-

(Scroll right to see the whole table)     

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**CTL_CONTROL** | | **O**| -- | | **CTLCL1**| ||
||Continue unloading |n1 |R| 6 |GIS[6] \(C529.1131=63).C529.7365|ConUnlCL130|27 | R510|

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **SEALS INFO** | | **O**| **-** | | **SEAINFSLI**| |-
|| Seals number|n..4 |R| 145 |CNT[145] \(C270.6069=16).C270.6066|SeaNumSLI2|-|-
|| **SEALS ID occurs 99**|| **R**| **-** || **SEAIDSID**|-|-
||SEALS ID Seals identity|an..20 |R| 10 |SEL[10] \(9308=0).C215.9302|SeaIdeSID1|-|-
||SEALS ID Seals identity LNG|a2 |O| 10 |SEL[10] \(9308=0).4517|SeaIdeSID1LNG|12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**GOODS ITEM occurs 999**|| **D**| **-** || **GOOITEGDS**|-|-
|32|Item number |n..5 |R| 92 |CST[92].1496 | IteNumGDS7 | - | R5, R7, TR1200
|33|Commodity code (taric code) |an..22 |D| 92 |CST[92].C246#1.7361 | ComCodTarCodGDS10 | - | C15, R60
||Type of declaration |an..9 |D| 92 |CST[92].C246#5.7361 | DecTypGDS15 | 31 | C45
|31|Goods description |an..260 |R| 93 |CST.FTX[93] \(4451=AAA).C108.4440#1 | GooDesGDS23 | -|-
||Goods description LNG |a2 |O| 93 |CST.FTX[93] \(4451=AAA).3453 | GooDesGDS23LNG | 12 | TR99
|35|Gross mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAB)(C174.6411=KGM).C174.6314| GroMasGDS46 | -|-
|38|Net mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAA)(C174.6411=KGM).C174.6314 | NetMasGDS48 | -|-
||Country of dispatch/export code |a2 |D| 94 |CST.LOC[94] \(3227=35).C517.3225 | CouOfDisGDS58 | 8 | C135
||Country of destination code |a2 |D| 94 |CST.LOC[94] \(3227=36).C517.3225| CouOfDesGDS59 | 8 | C140
|| **PRODUCED DOC/CERT occurs 99**|| **O**| **-** || **PRODOCDC2** |-|-
||PRODUCED DOC/CERT Document type|an..3 |R| 111 |CST.DOC[111] \(C002.1001=916).C002.1000| DocTypDC21 | 13 | -
|44|PRODUCED DOC/CERT Document reference|an..35|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1004| DocRefDC23 | -|-
||PRODUCED DOC/CERT Document reference LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.3453| DocRefDCLNG | 12 | TR99
||PRODUCED DOC/CERT Complement of information|an..26|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1366| ComOfInfDC25 | -|-
||PRODUCED DOC/CERT Complement of information LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1373| ComOfInfDC25LNG |12 | TR99
||**SPECIAL MENTIONS occurs 99**|| **O**| **-** || **SPEMENMT2** |-|-
|44|SPECIAL MENTIONS Additional information coded|an..5|R| 117 |CCST.TOD(4055=2).FTX[117] \(4451=ACB).C107.4441| AddInfCodMT23 | - | TR101
|44|SPECIAL MENTIONS Export from EC|n1|D| 115 |CST.TOD[115] \(4055=2).C100.4053| ExpFroECMT24 | 27 | C75, R75
|44|SPECIAL MENTIONS Export from country|a2|D| 115 |CST.TOD[115] \(4055=2).C100.1131| ExpFroCouMT25 | 63 | C75, R75
||**(CONSIGNOR) TRADER**|| **O**| **-** || **TRACONCO2** |- | **R10**
|02|(CONSIGNOR) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C080.3036#1| NamCO27 | -|-
|02|(CONSIGNOR) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C059.3042#1| StrAndNumCO222 | -|-
|02|(CONSIGNOR) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CZ).3251| PosCodCO223 | -|-
|02|(CONSIGNOR) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CZ).3164| CitCO224 | -|-
|02|(CONSIGNOR) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CZ).3207| CouCO225 | 8 | -
|02|(CONSIGNOR) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CZ).3229| NADLNGGTCO | 12 | TR99
|02|(CONSIGNOR) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CZ).C082.3039| TINCO259 | - | R012
||**(CONSIGNEE) TRADER**|| **D**| **-** || **TRACONCE2** |- | **R11, C2**
|08|(CONSIGNEE) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CN).C080.3036#1| NamCE27 | -|-
|08|(CONSIGNEE) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CN).C059.3042#1| StrAndNumCE222| -|-
|08|(CONSIGNEE) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CN).3251| PosCodCE223 | -|-
|08|(CONSIGNEE) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CN).3164| CitCE224 | -|-
|08|(CONSIGNEE) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CN).3207| CouCE225 | 8 | -
|08|(CONSIGNEE) TRADER NAD_LNG|a2|O| 97 |CST.NAD[97] \(3035=CN).3229| NADLNGGICE | 12 | TR99
|08|(CONSIGNEE) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CN).C082.3039| TINCE259 | - | R012
||**CONTAINERS occurs 99**|| **D**| **-** || **CONNR2** |- | **C55**
|31|CONTAINERS Container number|an..17|R| 105 |CST.RFF[105] \(C506.1153=AAQ).C506.1154| ConNumNR21 | -|-
||**PACKAGES occurs 99**|| **D**| **-** || **PACGS2** |-|-
|31|PACKAGES Marks & numbers of packages|an..42|D| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).C210.7102#1| MarNumOfPacGS21 | - | C60
||PACKAGES Marks & numbers of packages LNG|a2|O| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).8275| MarNumOfPacGS21LNG | 12 | TR99
|31|PACKAGES Kind of packages|an..3|R| 99 |CST.PAC[99] \(7224=6).C402.7077| KinOfPacGS23 | 17 | -
|31|PACKAGES Number of packages|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#1| NumOfPacGS24 | - | C60, R021
|31|PACKAGES Number of pieces|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#2| NumOfPieGS25| - | C60
||**SGI CODES occurs 9**|| **O**| **-** || **SGICODSD2** |-|-
||SGI CODES Sensitive goods code|n..2|O| 131 |CST.GIR[131] \(7297=3).C206#2.7402| SenGooCodSD22| 64|-
||SGI CODES Sensitive quantity|n..11,3|R| 131 |CST.GIR[131] \(7297=3).C206#1.7402| SenQuaSD23| -|-


## Unloading Remarks (IE44 – E_ULD_REM)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |||
|| **HEADER** | | **R**| -- | | **HEAHEA**| ||
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| -|-
|18|Identity of means of transport at departure (exp/trans)|an..27 |D|17 |TDT[17] \(8051=12).C222.8212| IdeOfMeaOfTraAtDHEA78 | - | TR02
|18|Identity of means of transport at departure LNG|a2 |O|18 |TDT(8051=12).TPL[18].C222.8453| IdeOfMeaOfTraAtDHEA78LNG | 12 | TR99
|18|Nationality of means of transport at departure|a2 |D|17 |TDT[17] \(8051=12).C222.8453| NatOfMeaOfTraAtDHEA80 | 8 | TR02
|5|Total number of items|n..5 |R|145 |CNT[145] \(C270.6069=5).C270.6066| TotNumOfIteHEA305 | -|-
|6|Total number of packages|n..7 |D|145 |CNT[145] \(C270.6069=11).C270.6066| TotNumOfPacHEA306 | - | TR02
|35|Total gross mass|n..11,3  |R|8 |MEA[8] \(6311=WT)(C502.6313=AAD)(C174.6411=KGM).C174.6314| TotGroMasHEA307 | -|-


(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DESTINATION) TRADER** | | **R**| -- | | **TRADESTRD**| ||
||Name |an..35 |D| 22 |NAD[22] \(3035=CPD).C080.3036#1| NamTRD7|  - | C160
||Street and number |an..35 |D| 22 |NAD[22] \(3035=CPD).C059.3042#1| StrAndNumTRD22| - | C160
||Postal code |an..9 |D| 22 |NAD[22] \(3035=CPD).3251| PosCodTRD23|- | C160
||City |an..35 |D| 22 |NAD[22] \(3035=CPD).3164| CitTRD24|- | C160
||Country code |a2 |D| 22 |NAD[22] \(3035=CPD).3207 |CouTRD25|8 | C160
||NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CPD).3229 |NADLNGRD|12 | TR99
||EORI-TIN (Turn) |an..17 |D| 22 |NAD[22] \(3035=CPD).C082.3039|TINTRD59 | - | C113

(Scroll right to see the whole table)     

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRESENTATION OFFICE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFPREOFFRES**| ||
||Reference number |an8 |R| 4 |LOC[4] \(3227=22).C517.3225|RefNumRES1|-|-

(Scroll right to see the whole table)     

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**UNLOADING REMARK** | | **R**| -- | | **UNLREMREM**| ||
||State of the seals OK |n1 |O| 28 |TOD(4055=5).FTX[28] \(4451=CLR).C107.4441|StaOfTheSeaOKREM19| 27 | R200/R340
||Unloading Remark |an..350|O| 28 |TOD(4055=5).FTX[28] \(4451=CLR).C108.4440#1|UnlRemREM53| -|-
||Unloading Remark LNG |a2|O| 28 |TOD(4055=5).FTX[28] \(4451=CLR).3453|UnlRemREM53LNG | 12 | TR99
||Conform |n1|R| 26 |TOD[26] \(4055=5).4215|ConREM65| - | R206
||Unloading completion |n1|R| 26 |TOD[26] \(4055=5).C100.4053|UnlComREM66| 27 | R186
||Unloading date |n8 |R| 26 |TOD[26] \(4055=5).C100.4052#1|UnlDatREM67| -|-

(Scroll right to see the whole table)     

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**RESULTS OF CONTROL occurs 9** | | **D**| -- | | **RESOFCON534**| - | **C210** |
||Control indicator |an2 |R| 11 |FTX[11] \(4451=ABV).C107.4441| ConInd424| 42 | TR03
||Pointer to the attribute|an..35|D| 11 |TOD(4055=5).FTX[28] \(4451=CLR).C108.4440#1|PoiToTheAttTOC5| - | TR05
||Description |an..140|O| 11 |FTX[11] \(4451=ABV).C108.4440#2 |DesTOC2 | - | TR06
||Corrected value |an..27|D| 11 |FTX[11] \(4451=ABV).C108.4440#4 |CorValTOC4| - | TR05, R150
||Description LNG |a2|D| 11 |FTX[11] \(4451=ABV).3453| DesTOC2LNG| 12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **SEALS INFO** | | **D**| **-** | | **SEAINFSLI**| |- | **C200**
||Seals number|n..4 |R| 145 |CNT[145] \(C270.6069=16).C270.6066|SeaNumSLI2|-|-
|| **SEALS ID occurs 99**|| **D**| **-** || **SEAIDSID**|- | **R206**
||SEALS ID Seals identity|an..20 |R| 10 |SEL[10] \(9308=0).C215.9302|SeaIdeSID1|-|-
||SEALS ID Seals identity LNG|a2 |O| 10 |SEL[10] \(9308=0).4517|SeaIdeSID1LNG|12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **GOODS ITEM occurs 999**|| **D**| **-** || **GOOITEGDS**|- | **C210/TR07/TR11**
|32|Item number |n..5 |R| 92 |CST[92].1496 | IteNumGDS7 | - | TR19
|33|Commodity code (taric code) |an..22 |D| 92 |CST[92].C246#1.7361 | ComCodTarCodGDS10 | - | C15, R060
|31|Goods description |an..260 |O| 93 |CST.FTX[93] \(4451=AAA).C108.4440#1 | GooDesGDS23 | -|-
||Goods description LNG |a2 |O| 93 |CST.FTX[93] \(4451=AAA).3453 | GooDesGDS23LNG | 12 | TR99
|35|Gross mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAB)(C174.6411=KGM).C174.6314| GroMasGDS46 | -|-
|38| Net mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAA)(C174.6411=KGM).C174.6314 | NetMasGDS48 | -|-
|| **PRODUCED DOC/CERT occurs 99**|| **O**| **-** || **PRODOCDC2** |- | **TR08**
||PRODUCED DOC/CERT Document type|an..3 |R| 111 |CST.DOC[111] \(C002.1001=916).C002.1000| DocTypDC21 | 13 | TR0103
|44|PRODUCED DOC/CERT Document reference|an..35|D| 111 |CST.DOC[111] \(C002.1001=916).C503.1004| DocRefDC23 | - | C902
||PRODUCED DOC/CERT Document reference LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.3453| DocRefDCLNG | 12 | TR99
||PRODUCED DOC/CERT Complement of information|an..26|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1366| ComOfInfDC25 | -|-
||PRODUCED DOC/CERT Complement of information LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1373| ComOfInfDC25LNG |12 | TR99
|| **RESULTS OF CONTROL occurs 199**|| **D**| **-** || **RESOFCONROC** |- | **C210, TR13/12/14**
||RESULTS OF CONTROL Control indicator|an2 |R| 93 |CST.FTX[93] \(4451=ABV).C107.4441| ConIndROC1 | 41 | TR03
||RESULTS OF CONTROL Pointer to the attribute|an..35 |D| 93 |CST.FTX[93] \(4451=ABV).C108.4440#1| PoiToTheAttROC51 | - | TR10, TR14, TR18
||RESULTS OF CONTROL Description|an..140 |O| 93 |CST.FTX[93] \(4451=ABV).C108.4440#2| DesROC2 | - | TR09
||RESULTS OF CONTROL Description LNG|a2 |D| 93 |CST.FTX[93] \(4451=ABV).3453| DesROC2LNG | 12 | TR99
||**CONTAINERS occurs 99**|| **O**| **-** || **CONNR2** |- | **TR08**
|31|CONTAINERS Container number|an..17|R| 105 |CST.RFF[105] \(C506.1153=AAQ).C506.1154| ConNumNR21 | -|-
|| **PACKAGES occurs 99**|| **D**| **-** || **PACGS2** |- | **TR08**
|31|PACKAGES Marks & numbers of packages|an..42|D| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).C210.7102#1| MarNumOfPacGS21 | - | C60
||PACKAGES Marks & numbers of packages LNG|a2|O| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).8275| MarNumOfPacGS21LNG | 12 | TR99
|31|PACKAGES Kind of packages|an..3|R| 99 |CST.PAC[99] \(7224=6).C402.7077| KinOfPacGS23 | 17 | -
|31|PACKAGES Number of packages|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#1| NumOfPacGS24 | - | C60, R021
|31|PACKAGES Number of pieces|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#2| NumOfPieGS25| - | C60
||**SGI CODES occurs 9**|| **O**| **-** || **SGICODSD2** |- |**R155/TR08**
|31|SGI CODES Sensitive goods code|n..2|O| 131 |CST.GIR[131] \(7297=3).C206#2.7402| SenGooCodSD22| 64 | R156
|31|SGI CODES Sensitive quantity|n..11,3|R| 131 |CST.GIR[131] \(7297=3).C206#1.7402| SenQuaSD23| -|-

## Write-off Notification (IE45 - E_WRT_NOT)
(Scroll right to see the whole table)


**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |- |-
||**HEADER** | | **R**| -- | | **HEAHEA**| -|-
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| -|-
||Write-off date|n8 |R| 5 |DTM[5] \(C507.2005=204).C507.2380 | WriOffDatHEA619| -|-

(Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| **--** | | **TRAPRIPC1**| ||
|50|Name |an..35 |R| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  -|-
|50|Street and number |an..35 |R| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| -|-
|50|Postal code |an..9 |R| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|-|-
|50|City |an..35 |R| 22 |NAD[22] \(3035=AF).3164| CitPC124|-|-
|50|Country code |a2 |R| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8|-
|50|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | R012
|50|Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904

(Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**GUARANTOR** | | **O**| | | **GUARANTOR**| ||
||Name |an..35 |R| 22 |NAD[22] \(3035=SX).C080.3036#1| NamGU620|  -|-
||Street and number |an..35 |R| 22 |NAD[22] \(3035=SX).C059.3042#1| StrAndNumGU621| -|-
||Postal code |an..9 |R| 22 |NAD[22] \(3035=SX).3251| PosCodGU622|-|-
||City |an..35 |R| 22 |NAD[22] \(3035=SX).3164| CitGU623|-|-
||Country code |a2 |R | 22|NAD[22] \(3035=SX).3207 |CouGU624|8 | -
||NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGGU|12 | TR99
||EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=SX).C082.3039 |TINGU626|- | R012

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| ||
|| Reference number |an8 |R| 4 |LOC[6] \(3227=118).C517.3225 |RefNumEPT1|- |-

## No release for Transit  (IE51 - E_REL_NOT)
(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | | ||
|| **HEADER** | | **R**| -- | | **HEAHEA**| - | **R134, R143**|
|7|Reference number (LRN)|an..22 |R| 12 |RFF[12] \(C506.1153=ABE).C506.1154| RefNumHEA4| -|-
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| -|-
|1|Type of declaration | an..9|R| 2 |BGM[2].C002.1000| TypOfDecHEA24|  31 | R909, R911
|17A|Country of destination code|a2 |D| 4|LOC[4] \(3227=36).C517.3225|CouOfDesCodHEA30 | 8 | C140
|30|Agreed location of goods, code|an..17 |D| 4|LOC[4] \(3227=14).C517.3225|AgrLocOfGooCodHEA38 | - | C100, R41
|30|Agreed location of goods|an..35 |D| 4|LOC[4] \(3227=14).C517.3224|AgrLocOfGooHEA39 | - | C100, R41
||Agreed location of goods LNG|a2 |O| 4|LOC[4] \(3227=14).5479|AgrLocOfGooHEA39LNG | 12 | TR99
|30|Authorised location of goods, code|an..17 |D| 4|LOC[4] \(3227=14).C519.3223|AutLocOfGooCodHEA41 | - | C100, R41
|27|Place of loading, code|an..17 |D| 4|LOC[4] \(3227=9).C517.3225|PlaOfLoaCodHEA46 | - | C191
|15A|Country of dispatch/export code|a2 |D| 4|LOC[4] \(3227=35).C517.3225|CouOfDisCodHEA55 | 8 | C135
||Customs sub place|an..17 |D| 4|LOC[4] \(3227=26).C517.3225|CusSubPlaHEA66 | - | C100, R41
|26|Inland transport mode|n..2 |O| 17|TDT[17] \(8051=1).C220.8067| InlTraModHEA75 | 18 | -
|25|Transport mode at border|n..2 |D| 17|TDT[17] \(8051=11).C220.8067| TraModAtBorHEA76 | 18 | C599
|18|Identity of means of transport at departure (exp/trans)|an..27 |D|17 |TDT[17] \(8051=12).C222.8212| IdeOfMeaOfTraAtDHEA78 | - | TR0035, TR9090, TR02
|18|Identity of means of transport at departure LNG|a2 |O|18 |TDT(8051=12).TPL[18].C222.8453| IdeOfMeaOfTraAtDHEA78LNG | 12 | TR99
|18|Nationality of means of transport at departure|a2 |D|17 |TDT[17] \(8051=12).C222.8453| NatOfMeaOfTraAtDHEA80 | 8 | TR02, TR0035, TR9095
|21|Identity of means of transport crossing border|an..27 |D|17 |TDT[17] \(8051=11).C222.8212| IdeOfMeaOfTraCroHEA85 | - | C011
||Identity of means of transport crossing border LNG|a2 |O|18 |TDT(8051=11).TPL[18].C222.8453| IdeOfMeaOfTraCroHEA85LNG |12 | TR99
|21|Nationality of means of transport at crossing border|a2 |D|17 |TDT[17] \(8051=11).C222.8453| NatOfMeaOfTraCroHEA87 | 8 | R36, C10
||Type of means of transport crossing border|n..2 |O|17 |TDT[17] \(8051=11).C228.8179| TypOfMeaOfTraCroHEA88 |18 | -
|19|Containerised indicator|n1 |R|6 |GIS[6] \(C529.1131=109).C529.7365| ConIndHEA96 |27 | R230
||Dialog language indicator at departure | a2 |O| 11 |FTX[11] \(4451=ACB).3453| DiaLanIndAtDepHEA254| 12 | R100
||NCTS accompanying document language code|a2 |R|11 |FTX[11] \(4451=ALL).3453| NCTSAccDocHEA601LNG |12 | -
|5|Total number of items|n..5 |R|145 |CNT[145] \(C270.6069=5).C270.6066| TotNumOfIteHEA305 | -|-
|6|Total number of packages|n..7 |O|145 |CNT[145] \(C270.6069=11).C270.6066| TotNumOfPacHEA306 | - | R105, TR02
|35| Total gross mass|n..11,3 |R|8 |MEA[8] \(6311=WT)(C502.6313=AAD)(C174.6411=KGM).C174.6314| TotGroMasHEA307 | -|-
|50|Declaration date|n8 |R|5 |DTM[5] \(C507.2005=137).C507.2380| DecDatHEA383 | -|-
|50|Declaration place|an..35 |R|4 |LOC[4] \(3227=91).C517.3224| DecPlaHEA394 | -|-
|50|Declaration place LNG|a2 |O|4 |LOC[4] \(3227=91).5479| DecPlaHEA394LNG | 12 | TR99
||No release motivation|an..350 |O|11 |FTX[11] \(4451=ABQ).C108.4440#1| NoRelMotHEA272 | -|-
||No release motivation LNG|a2 |O|11 |FTX[11] \(4451=ABQ).3453| NoRelMotHEA272LNG | 12 | TR99
||Specific Circumstance Indicator|a1 |D|12 |RFF[12] \(C506.1153=AMJ).C506.1154| SpeCirIndHEA1 | 96 | C186, C825
||Transport charges/ method of payment|a1 |D|11 |FTX[11] \(4451=PAI).4453| TraChaMetOfPayHEA1 | 116 | C186
||Commercial reference number|an..70 |D|7 |FII[7] \(3035=XX).C088.3436| ComRefNumHEA | - | C186, C547, R876
||Security|n1 |O|6 |GIS[6] \(C529.1131=187).C529.7365| SecHEA358 | 117 | R229
||Conveyance reference number|an..35 |O|11 |FTX[11] \(4451=ACR).C108.4440#1| ConRefNumHEA | - | C531
||Place of unloading, code|an..35 |D|4 |LOC[4] \(3227=58).C517.3224| CodPlUnHEA357 | - | C186, C589
||Place of unloading, LNG|a2 |O|4 |LOC[4] \(3227=58).C517.3225| CodPlUnHEA357LNG | 12 | TR0099

(Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| | | **TRAPRIPC1**| ||
|50| Name |an..35 |D| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  - | C50, NC50
|50|Street and number |an..35 |D| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C50, NC50
|50|Postal code |an..9 |D| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|- | C50, NC50
|50|City |an..35 |D| 22 |NAD[22] \(3035=AF).3164| CitPC124|- | C50, NC50
|50|Country code |a2 |D| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8 | C50, NC50
|50|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |D| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | C111, C236, NR1|
|50|Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904, NR1

Scroll right to see the whole table)    

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNOR) TRADER** | | **O**| | | **TRACONCO1**| |- | **R10**
|2| Name |an..35 |R| 22 |NAD[22] \(3035=CZ).C080.3036#1| NamCO17|  -|-
|2|Street and number |an..35 |R| 22 |NAD[22] \(3035=CZ).C059.3042#1| StrAndNumCO122| -|-
|2|Postal code |an..9 |R| 22 |NAD[22] \(3035=CZ).3251| PosCodCO123|-|-
|2|City |an..35 |R| 22 |NAD[22] \(3035=CZ).3164| CitCO124|-|-
|2|Country code |a2 |R| 22 |NAD[22] \(3035=CZ).3207 |CouCO125|8 | -
|2|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CZ).3229| NADLNGCO |12 | TR99
|2|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CZ).C082.3039 |TINCO159|- | -

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(CONSIGNEE) TRADER** | | **D**| | | **TRACONCE1**|- | **R11, C1**
|8|Name |an..35 |R| 22 |NAD[22] \(3035=CN).C080.3036#1| NamCE17|  -|-
|8|Street and number |an..35 |R| 22 |NAD[22] \(3035=CN).C059.3042#1| StrAndNumCE122| -|-
|8|Postal code |an..9 |R| 22 |NAD[22] \(3035=CN).3251| PosCodCE123|-|-
|8|City |an..35 |R| 22 |NAD[22] \(3035=CN).3164| CitCE124|-|-
|8|Country code |a2 |R| 22 |NAD[22] \(3035=CN).3207 |CouCE125| 8 | -
|8|NAD_LNG |a2 |O| 22 |NAD[22] \(3035=CN).3229| NADLNGCE |12 | TR99
|8|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=CN).C082.3039| TINCE159 | -|-

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(AUTHORISED CONSIGNEE) TRADER** | | **O**|  | | **TRAAUTCONTRA**|- | **R15**
||EORI-TIN (Turn) |an..17 |R| 22 |NAD[22] \(3035=TD).C082.3039 |TINTRA59|-|-

(Scroll right to see the whole table)      

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(DEPARTURE) CUSTOMS OFFICE** | | **R**|-- | | **CUSOFFDEPEPT**| -|-
|C| Reference number |an8 |R| 4 |LOC[4] \(3227=118).C517.3225|RefNumEPT1|- | R901

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(TRANSIT) CUSTOMS OFFICE occurs 9** | | **D**| **-** | | **CUSOFFTRARNS**|- | **C30, R902**
|51| Reference number |an8 |R| 4 |LOC[4] \(3227=50).C517.3225|RefNumRNS1|- | R906, R907, R908, R910
||Arrival Time |n12 |D| 4 |LOC[4] \(3227=50).C519.3223|ArrTimTRACUS085|- |C598, R660

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DESTINATION) CUSTOMS OFFICE** | | **R**| **-** | | **CUSOFFDESEST**| -|-
|53|Reference number |an8 |R| 4 |LOC[4] \(3227=45).C517.3225|RefNumEST1|- | R901, R904, R905

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **CONTROL RESULT** | | **R**| **-** | | **CONRESERS**| |-
|D|Control date |n8 |R| 5 |DTM[5] \(C507.2005=9).C507.2380|ConDatERS14 ||
|D|Control result code|an2 |R| 11 |FTX[11] \(4451=ADO).C107.4441|ConResCodERS16 | 47 | R903
|D|Date limit|n8 |O| 5 |DTM[5] \(C507.2005=268).C507.2380|DatLimERS69|-|-

(Scroll right to see the whole table)     

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**RESULTS OF CONTROL occurs 9** | | **O**| -- | | **RESOFCON534**| - | **R145** |
||Control indicator |an2 |R| 11 |FTX[11] \(4451=ABV).C107.4441| ConInd424| 42 | TR03
||Description |an..140|O| 11 |FTX[11] \(4451=ABV).C108.4440#2 |DesTOC2 | - | TR06
||Description LNG |a2|D| 11 |FTX[11] \(4451=ABV).3453 |DesTOC2LNG | 12 | TR99

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**REPRESENTATIVE** | | **O**| **-** | | **REPREP**| |-
|50|Name|an..35 |R| 22 |NAD[22] \(3035=AH).C080.3036#1|NamREP5|-|-
|50|Representative capacity|an..35 |O| 11 |FTX[11] \(4451=ACP).C108.4440#1|RepCapREP18|-|-
|50|Representative capacity LNG |a2 |O| 11 |FTX[11] \(4451=ACP).3453|RepCapREP18LNG |12 | TR99

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**SEALS INFO** | | **O**| **-** | | **SEAINFSLI**|- | **R165**
|D|Seals number|n..4 |R| 145 |CNT[145] \(C270.6069=16).C270.6066|SeaNumSLI2|-|-
|| **SEALS ID occurs 99**|| **R**| **-** || **SEAIDSID**|-|-
|D|SEALS ID Seals identity|an..20 |R| 10 |SEL[10] \(9308=0).C215.9302|SeaIdeSID1|-|-
||SEALS ID Seals identity LNG|a2 |O| 10 |SEL[10] \(9308=0).4517|SeaIdeSID1LNG|12 | TR99

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**GUARANTEE occurs 9**|| **R**| **-** || **GUAGUA**|-|-
|52|Guarantee type |an1 |R| 12 |RFF[12] \(C506.1153=ABL).C506.1154|GuaTypGUA1|51 | C900
||**GUARANTEE REFERENCE occurs 99**|| **D**| **-** || **GUAREFREF**|- | **C085**
|52|GUARANTEE REFERENCE Guarantee reference number (GRN) |an..24 |D| 14 |RFF(C506.1153=ABL).PAC[14] \(7224=1).C402.7064#1|GuaRefNumGRNREF1|- | C125, TR301
|52|GUARANTEE REFERENCE Other guarantee reference |an..35 |D| 14 |RFF(C506.1153=ABL).PAC[14]\(7224=1).C402.7064#2|OthGuaRefREF4|- | C130, R900
|52|GUARANTEE REFERENCE Access code |an4 |D| 14 |RFF(C506.1153=ABL).PAC[14] \(7224=1).C402.7077|AccCodREF6|- | C86
||**GUARANTEE REFERENCE - VALIDITY LIMITATION EC**|| **O**| **-** || **VALLIMECVLE**|-|-
|52|GUARANTEE REFERENCE - VALIDITY LIMITATION EC. Not valid for EC|n1 |R| 15 |RFF(C506.1153=ABL).PAC(7224=1).PCI[15] \(4233=19).C210.7102#1| NotValForECVLE1 |27 | R230
||**GUARANTEE REFERENCE - VALIDITY LIMITATION NON EC occurs 99**|| **O**| **-** || **VALLIMNONECLIM**|-|-
|52|GUARANTEE REFERENCE - VALIDITY LIMITATION NON EC. Not valid for other contracting parties |a2 |R| 15 |RFF(C506.1153=ABL).PAC(7224=1).PCI[15] \(4233=28).C210.7102#1| NotValForOthConPLIM2 |71 | R231

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**GOODS ITEM occurs 999**|| **R**| **-** || **GOOITEGDS**|-|-
|32|Item number |n..5 |R| 92 |CST[92].1496 | IteNumGDS7 | - | R5, R7, TR1200
|33|Commodity code (taric code) |an..22 |D | 92 |CST[92].C246#1.7361 | ComCodTarCodGDS10 | - | C15, R60, R470
|1|Type of declaration |an..9 |D| 92 |CST[92].C246#5.7361 | DecTypGDS15 | 31 | C45
|31|Goods description |an..260 |R| 93 |CST.FTX[93] \(4451=AAA).C108.4440#1 | GooDesGDS23 | -|-
||Goods description LNG |a2 |O| 93 |CST.FTX[93] \(4451=AAA).3453 | GooDesGDS23LNG | 12 | TR99
|35|Gross mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAB)(C174.6411=KGM).C174.6314| GroMasGDS46 | - | R700
|38|Net mass |n..11,3 |O| 96 |CST.MEA[96] \(6311=WT)(C502.6313=AAA)(C174.6411=KGM).C174.6314 | NetMasGDS48 | -|-
|15A|Country of dispatch/export code |a2 |D| 94 |CST.LOC[94] \(3227=35).C517.3225 | CouOfDisGDS58 | 8 | C135
|17A|Country of destination code |a2 |D| 94 |CST.LOC[94] \(3227=36).C517.3225| CouOfDesGDS59 | 8 | C140
||Transport charges/ Method of Payment |a1 |D| 98 |CST.TDT[98] \(8051=10).C228.8179| MetOfPayGDI12 | 116 | C186, C576, TR9120
||Commercial Reference Number|an..70 |D| 93 |CST.FTX[93] \(4451=IND).C108.4440#1| ComRefNumGIM1 | - | C186, C547, R876
||UN dangerous goods code|an4 |O| 98 |CST.TDT[98] \(8051=10).C222.8213| UNDanGooCodGDI1 | 101 | C186
||**PREV ADMIN REF occurs 9**|| **D**| **-** || **PREADMREFAR2** |- | **C035**
|40|PREV ADMIN REF Previous document type|an..6 |R| 111 |CST.DOC[111] \(C002.1001=190).C002.1000| PreDocTypAR21 | - | R20, TR100
|40|PREV ADMIN REF Previous document reference|an..35 |R| 111 |CST.DOC[111] \(C002.1001=190).C503.1004| PreDocRefAR26 | -|-
||PREV ADMIN REF Previous document reference LNG|a2 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.3453| PreDocRefLNG | 12 | TR99
|40|PREV ADMIN REF Complement of information |an..26 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.1366| ComOfInfAR29| -|-
||PREV ADMIN REF Complement of information LNG |a2 |O| 111 |CST.DOC[111] \(C002.1001=190).C503.1373| ComOfInfAR29LNG| 12 | TR99
||**PRODUCED DOC/CERT occurs 99**|| **D**| **-** || **PRODOCDC2** |- | **C903, C547**
|44|PRODUCED DOC/CERT Document type|an..4 |R| 111 |CST.DOC[111] \(C002.1001=916).C002.1000| DocTypDC21 | 13 | C901, TR0103
|44|PRODUCED DOC/CERT Document reference|an..35|D| 111 |CST.DOC[111] \(C002.1001=916).C503.1004| DocRefDC23 | - | C902
||PRODUCED DOC/CERT Document reference LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.3453| DocRefDCLNG | 12 | TR99
|44|PRODUCED DOC/CERT Complement of information|an..26|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1366| ComOfInfDC25 | -|-
||PRODUCED DOC/CERT Complement of information LNG|a2|O| 111 |CST.DOC[111] \(C002.1001=916).C503.1373| ComOfInfDC25LNG |12 | TR99
||**SPECIAL MENTIONS occurs 99**|| **O**| **-** || **SPEMENMT2** |- | **R27**
|44|SPECIAL MENTIONS Additional information|an..70|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).C108.4440#1| AddInfMT21 | -|-
|44|SPECIAL MENTIONS Additional information LNG|a2|O| 117 |CST.TOD(4055=2).FTX[117] \(4451=ACB).3453| AddInfMT21LNG | 12 | TR99
|44|SPECIAL MENTIONS Additional information coded|an..5|O| 117 |CCST.TOD(4055=2).FTX[117] \(4451=ACB).C107.4441| AddInfCodMT23 | - | TR101
|44|SPECIAL MENTIONS Export from EC|n1|D| 115 |CST.TOD[115] \(4055=2).C100.4053| ExpFroECMT24 | 27 | C75, R75
|44|SPECIAL MENTIONS Export from country|a2|D| 115 |CST.TOD[115] \(4055=2).C100.1131| ExpFroCouMT25 | 63 | C75, R75
||**RESULTS OF CONTROL occurs 9**|| **O**| **-** || **RESOFCONROC** |-|-
||RESULTS OF CONTROL Control indicator|an2|R| 93 |CST.FTX[93] \(4451=ABV).C107.4441| ConIndROC1 | 41 | TR03
||RESULTS OF CONTROL Pointer to the attribute|an..35|D| 93 |CST.FTX[93] \(4451=ABV).C108.4440#1| PoiToTheAttROC51 | - | TR10, TR14
||RESULTS OF CONTROL Description|an..140|O| 93 |CST.FTX[93] \(4451=ABV).C108.4440#2| **DesROC2** | - | TR09
||RESULTS OF CONTROL Description LNG |a2|D| 93 |CST.FTX[93] \(4451=ABV).3453| DesROC2LNG | 12 | TR99
||**(CONSIGNOR) TRADER**|| **O**| **-** || **TRACONCO2** |- : **R10**|||
|2|(CONSIGNOR) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C080.3036#1| NamCO27 | -|-
|2|(CONSIGNOR) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CZ).C059.3042#1| StrAndNumCO222 | -|-
|2|(CONSIGNOR) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CZ).3251| PosCodCO223 | -|-
|2|(CONSIGNOR) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CZ).3164| CitCO224 | -|-
|2|(CONSIGNOR) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CZ).3207| CouCO225 | 8 | -
|2|(CONSIGNOR) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CZ).3229| NADLNGGTCO | 12 | TR99
|2|(CONSIGNOR) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CZ).C082.3039| TINCO259 | -|-
||**(CONSIGNEE) TRADER**|| **D**| **-** || **TRACONCE2** |- | **R11, CO02**
|8|(CONSIGNEE) TRADER Name|an..35|R| 97 |CST.NAD[97] \(3035=CN).C080.3036#1| NamCE27 | -|-
|8|(CONSIGNEE) TRADER Street and number|an..35|R| 97 |CST.NAD[97] \(3035=CN).C059.3042#1| StrAndNumCE222| -|-
|8|(CONSIGNEE) TRADER Postal code|an..9|R| 97 |CST.NAD[97] \(3035=CN).3251| PosCodCE223 | -|-
|8|(CONSIGNEE) TRADER City|an..35|R| 97 |CST.NAD[97] \(3035=CN).3164| CitCE224 | -|-
|8|(CONSIGNEE) TRADER Country code|a2|R| 97 |CST.NAD[97] \(3035=CN).3207| CouCE225 | 8 | -
|8|(CONSIGNEE) TRADER NAD_LNG|a2|O| 97 |CCST.NAD[97] \(3035=CN).3229| NADLNGGICE | 12 | TR99
|8|(CONSIGNEE) TRADER EORI-TIN (Turn)|an..17|O| 97 |CST.NAD[97] \(3035=CN).C082.3039| TINCE259 | -|-
||**CONTAINERS occurs 99**|| **D**| **-** || **CONNR2** |- | **C55**
|31|CONTAINERS Container number|an..17|R| 105 |CST.RFF[105] \(C506.1153=AAQ).C506.1154| ConNumNR21 | - | C60
|| **PACKAGES occurs 99**|| **R**| **-** || **PACGS2** |-|-
|31|PACKAGES Marks & numbers of packages|an..42|D| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).C210.7102#1| MarNumOfPacGS21 | - | C60
||PACKAGES Marks & numbers of packages LNG|a2|O| 100 |CST.PAC(7224=6).PCI[100] \(4233=28).8275| MarNumOfPacGS21LNG | 12 | TR99
|31|PACKAGES Kind of packages|an..3|R| 99 |CST.PAC[99] \(7224=6).C402.7077| KinOfPacGS23 | 17 | -
|31|PACKAGES Number of packages|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#1| NumOfPacGS24 | - | C60, R021, TR0022
|31|PACKAGES Number of pieces|n..5|D| 99 |CST.PAC[99] \(7224=6).C402.7064#2| NumOfPieGS25| - | C60
||**SGI CODES occurs 9**|| **O**| **-** || **SGICODSD2** |- | **R155**
|31|SGI CODES Sensitive goods code|n..2|O| 131 |CST.GIR[131] \(7297=3).C206#2.7402| SenGooCodSD22| 64 | R156
|31|SGI CODES Sensitive quantity|n..11,3|R| 131 |CST.GIR[131] \(7297=3).C206#1.7402| SenQuaSD23| -|-
||**(CONSIGNOR-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACORSECGOO021** |- | **C186, C187**
||Name|an..35|D| 97 |NAD[97] \(3035=GM).C080.3036#1| NamTRACORSECGOO025 | - | C501
||Street and number|an..35|D| 97 |NAD[97] \(3035=GM).C059.3042#1| StrNumTRACORSECGOO027 | - | C501
||Postal code|an..9|D| 97 |NAD[97] \(3035=GM).3251| PosCodTRACORSECGOO026 | - | C501
||City|an..35|D| 97 |NAD[97] \(3035=GM).3164| CitTRACORSECGOO022 | - | C501
||Country code|a2|D| 97 |NAD[97] \(3035=GM).3207| CouCodTRACORSECGOO023 | 8 | C501
||NAD_LNG|a2|O| 97 |NAD[97] \(3035=GM).3229| TRACORSECGOO021LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 97 |NAD[97] \(3035=GM).C082.3039| TINTRACORSECGOO028 | - | C572
||**(CONSIGNEE-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACONSECGOO013** |- | **C186, C188**
||Name|an..35|D| 97 |NAD[972] \(3035=DP).C080.3036#1| NamTRACONSECGOO017 | - | C501
||Street and number|an..35|D| 97 |NAD[972] \(3035=DP).C059.3042#1| StrNumTRACONSECGOO019 | - | C501
||Postal code|an..9|D| 97 |NAD[972] \(3035=DP).3251| PosCodTRACONSECGOO018 | - | C501
||City|an..35|D| 97 |NAD[972] \(3035=DP).3164| CityTRACONSECGOO014 | - | C501
||Country code|a2|D| 97 |NAD[972] \(3035=DP).3207| CouCodTRACONSECGOO015 | 8 | C501
||NAD_LNG|a2|O| 97 |NAD[97] \(3035=DP).3229| TRACONSECGOO013LNG | 12 | TR099
||EORI-TIN (Turn)|an..17|D| 97 |NAD[97] \(3035=DP).C082.3039| TINTRACONSECGOO020 | - | C596

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**ITINERARY occurs 99**|| **D**| **-** || **ITI** |- | **C186, C587**
||Country of routing code|a2|R| 9 |EQD[9] \(8053=CH).C237.3207| CouOfRouCodITI1 | 8 | -

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(CARRIER) TRADER occurs 1**|| **D**| **-** || **CARTRA100** |- | **C186, R181**
||Name|an..35|D| 22 |NAD[22] \(3035=GA).C080.3036#1| NamCARTRA121 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=GA).C059.3042#1| StrAndNumCARTRA254 | - | C501
||Postal code|an..9|D| 22 |NAD[22] \(3035=GA).3251 | PosCodCARTRA121 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=GA).3164| CitCARTRA789 | - | C501
||Country code|a2|D| 22 |NAD[22] \(3035=GA).3207| CouCodCARTRA587 | 8 | C501
||NAD_LNG|a2|O| 22 |NAD[22] \(3035=GA).3229| NADCARTRA121 | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=GA).C082.3039| TINCARTRA254 | -|-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNOR-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACORSEC037** |- | **C186, C187**
|| Name|an..35|D| 22 |NAD[22] \(3035=GL).C080.3036#1| NameTRACORSEC043 | - | C501
|| Street and number|an..35|D| 22 |NAD[22] \(3035=GL).C059.3042#1| StrNumTRACORSEC043 | - | C501
|| Postal code|an..9|D| 22 |NAD[22] \(3035=GL).3251 | PosCodTRACORSEC042 | - | C501
|| City|an..35|D| 22 |NAD[22] \(3035=GL).3164| CitTRACORSEC038 | - | C501
|| Country code|a2|D| 22 |NAD[22] \(3035=GL).3207| CouCodTRACORSEC039| 8 | C501
|| NAD_LNG|a2|O| 22 |NAD[22] \(3035=GL).3229| TRACORSEC037LNG | 12 | TR0099
|| EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=GL).C082.3039| TINTRACORSEC044 | - | C572

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(CONSIGNEE-SECURITY) TRADER occurs 1**|| **D**| **-** || **TRACONSEC029** |- | **C186, C188**
||Name|an..35|D| 22 |NAD[22] \(3035=UC).C080.3036#1| NameTRACONSEC033 | - | C501
||Street and number|an..35|D| 22 |NAD[22] \(3035=UC).C059.3042#1| StrNumTRACONSEC035 | - | C501
||Postal code|an..9|D| 22 |NAD[22] \(3035=UC).3251| PosCodTRACONSEC034 | - | C501
||City|an..35|D| 22 |NAD[22] \(3035=UC).3164| CitTRACONSEC030| - | C501
||Country code|a2|D| 22 |NAD[22] \(3035=UC).3207| CouCodTRACONSEC031| 8 | C501
||NAD_LNG|a2|O| 22 |NAD[22] \(3035=UC).3229| TRACONSEC029LNG | 12 | TR0099
||EORI-TIN (Turn)|an..17|D| 22 |NAD[22] \(3035=UC).C082.3039| TINTRACONSEC036 | - | C596

## Guarantee not valid (IE55 – E_GUA_INV)
(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |-  ||
||**HEADER** | | **R**| -- | | **HEAHEA**| - ||
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2].C106.1004 | DocNumHEA5| -|-

(Scroll right to see the whole table)  

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(PRINCIPAL) TRADER** | | **R**| | | **TRAPRIPC1**| ||
|50|Name |an..35 |R| 22 |NAD[22] \(3035=AF).C080.3036#1| NamPC17|  - | C160
|50|Street and number |an..35 |D| 22 |NAD[22] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C160
|50|Postal code |an..9 |D| 22 |NAD[22] \(3035=AF).3251| PosCodPC123|- | C160
|50|City |an..35 |D| 22 |NAD[22] \(3035=AF).3164| CitPC124|- | C160
|50|Country code |a2 |D| 22 |NAD[22] \(3035=AF).3207 |CouPC125|8 | C160
|50| NAD_LNG |a2 |O| 22 |NAD[22] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |O| 22 |NAD[22] \(3035=AF).C082.3039 |TINPC159|- | R012|

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| ||
||Reference number |an8 |R| 4 |LOC[4] \(3227=118).C517.3225 |RefNumEPT1|- |-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSDEC**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(GUARANTEE REFERENCE occurs 99** | | **R**| -- | | **GUAREF2**| ||
|52| Guarantee reference number (GRN) |an..24 |R| 14 |RFF(C506.1153=ABK).PAC[14] \(C531.7075=1).C402.7064#1 |GuaRefNumGRNREF21|- |-
|| **INVALID GUARANTEE REASON** | | **R**| -- | | **INVGUARNS**| ||
|| Invalid guarantee reason code |an..3 |R| 16 |RFF(C506.1153=ABK).PAC(7224=1).PCI.FTX[16] \(4451=AUT).C107.4441 |InvGuaReaCodRNS11| 52 | - |
|| Invalid guarantee reason  |an..350 |O| 16 |RFF(C506.1153=ABK).PAC(7224=1).PCI.FTX[16] \(4451=AUT).C108.4440#1 |InvGuaReaRNS12| - |-
|| Invalid guarantee reason LNG |a2 |O| 16 |RFF(C506.1153=ABK).PAC(7224=1).PCI.FTX[16] \(4451=AUT).3453 |InvGuaReaRNS12LNG | - | TR99 |

## Unloading remarks rejection (IE58 – E_ULD_REJ)
(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |  ||
|| **HEADER** | | **R**| -- | | **HEAHEA**| - |-
|| Document/reference number (MRN)|an..21 |R| 2 |BGM[2] \(1225=11).C106.1004 | DocNumHEA5| -|-
||Unloading remarks rejection date|n8 |R| 3 |DTM[3] \(C507.2005=357).C507.2380 | UnlRemRejDatHEA218| -|-
||Unloading remarks rejection reason|an..350 |O| 4 |FTX[4] \(4451=ACD).C108.4440#1| UnlRemRejReaHEA280| -|-
||Unloading remarks rejection reason LNG|a2 |O| 4 |FTX[4] \(4451=ACD).3453| UnlRemRejReaHEA280LNG| 12 | TR99

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**FUNCTIONAL ERROR occurs 999**|| **D**| **-** || **FUNERRER1** |- | **R123**
||Error type| n2|R| 4 |FTX[4] \(4451=AAO).C107.4441|ErrTypER11| 49 | -
||Error pointer| an..210|R| 4 |FTX[4] \(4451=AAO).C108.4440#1|ErrPoiER12| 100 | -
||Error reason| an..6|O| 4 |FTX[4] \(4451=AAO).C108.4440#4|ErrReaER13| -|-
||Original attribute value| an..140|O| 4 |FTX[4] \(4451=AAP).C108.4440#1|OriAttValER14| -|-

## Control decision notification  (IE60 – E_CTR_DEC)
(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |  ||
||**HEADER** | | **R**| -- | | **HEAHEA**| - |-
||Document/reference number (MRN)|an..21 |R| 2 |BGM[2] \(1225=11).C106.1004 | DocNumHEA5| -|-
||Date of control notification|n8 |R| 3 | DTM[3] \(C507.2005=184).C507.2380 | DatOfConNotHEA148| -|-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| -- | | **TRAPRIPC1**| ||
|50| Name |an..35 |R| 9 |NAD[9] \(3035=AF).C080.3036#1| NamPC17|  -|-
|50|Street and number |an..35 |R| 9 |NAD[9] \(3035=AF).C059.3042#1| StrAndNumPC122| -|-
|50|Postal code |an..9 |R| 9 |NAD[9] \(3035=AF).3251| PosCodPC123|-|-
|50|City |an..35 |R| 9 |NAD[9] \(3035=AF).3164| CitPC124|-|-
|50|Country code |a2 |R| 9 |NAD[9] \(3035=AF).3207 |CouPC125|8|-
|50|NAD_LNG |a2 |O| 9 |NAD[9] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |O| 9 |NAD[9] \(3035=AF).C082.3039 |TINPC159|- | R012
|50|Holder ID TIR |an..17 |D| 9 |NAD[9] \(3035=AF).C080.3036#2 |HITPC126|- | C904|

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| ||
||Reference number |an8 |R| 6 |LOC[6] \(3227=118).C517.3225 |RefNumEPT1|- |-

## XML NCK (IE917 – C_XML_NCK)
(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |- ||
||**HEADER** | | **R**| -- | | **HEAHEA**| - |-
||Original message identification (ICR)|an..14 |R| 4 |RFF[12] \(1153=ABO).C506.1154| OriMesIdeMES22| -|-
||Document/reference number (MRN)|an..21 |D| 2 |BGM[2] \(1225=11).C106.1004| DocNumHEA5| - | TR9250
||Reference number (LRN)|an..22 |D| 4 |RFF[12] \(1153=ABE).C506.1154| RefNumHEA4| -|-

(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping FUNACK**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**FUNCTIONAL ERROR**|| **R**| **-** || **FUNERRER1** |-|-
||Error type| n2|R| 4 |FTX[4] \(4451=AAO).C107.4441|ErrTypER11| 49 | -
||Error pointer| an..210|R| 4 |FTX[4] \(4451=AAO).C108.4440#1|ErrPoiER12| 100|-
||Error reason| an..140|O| 6 |FTX[4] \(4451=AAO).C108.4440#4|ErrReaER13| -|-
||Original attribute value| an..140|O| 4 |FTX[4] \(4451=AAP).C108.4440#1|OriAttValER14| - | TR9250

## Positive Acknowledgement (IE928 - E_POS_ACK)
(Scroll right to see the whole table)

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
||**MESSAGE** (as per IE15 - E_DEC_DAT)| | **R** | -- | | |- ||
||**HEADER** | | **R**| -- | | **HEAHEA**| - |-
|7|Reference number (LRN)|an..22 |R| 12 |RFF[12] \(C506.1153=ABE).C506.1154| RefNumHEA4| -|-

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(PRINCIPAL) TRADER** | | **R**| -- | | **TRAPRIPC1Type**| ||
|50| Name |an..35 |D| 9 |NAD[9] \(3035=AF).C080.3036#1| NamPC17|  - | C160
|50|Street and number |an..35 |D| 9 |NAD[9] \(3035=AF).C059.3042#1| StrAndNumPC122| - | C160
|50|Postal code |an..9 |D| 9 |NAD[9] \(3035=AF).3251| PosCodPC123|- | C160
|50|City |an..35 |D| 9 |NAD[9] \(3035=AF).3164| CitPC124|- | C160
|50|Country code |a2 |D| 9 |NAD[9] \(3035=AF).3207 |CouPC125|8 | C160
|50|NAD_LNG |a2 |O| 9 |NAD[9] \(3035=AF).3229 |NADLNGPC|12 | TR99
|50|EORI-TIN (Turn) |an..17 |O| 9 |NAD[9] \(3035=AF).C082.3039 |TINPC159|- |-
|50|Holder ID TIR |an..17 |D| 22 |NAD[22] \(3035=AF).C080.3036#2 |HITPC126|- | C904|

(Scroll right to see the whole table)   

**SAD box**| **Message element** | **Date type**| **Data requirement**| **EDIFACT position** | **EDIFACT mapping CUSRES**| **XML mapping** | **Code list** | **Conditions/rules**
---|---|---|---|---|---|---|---|---
|| **(DEPARTURE) CUSTOMS OFFICE** | | **R**| -- | | **CUSOFFDEPEPT**| ||
|| Reference number |an8 |R| 6 |LOC[6] \(3227=118).C517.3225 |RefNumEPT1|- |-
