
---
title: Get support and help | Common Transit Convention API end-to-end service guide
weight: 88
---

# Test scenarios 1

Here is a list of test scenarios with test data.


## Declaration IE015: Safety and security simplified declaration with office of transit -  authorised location and missing place of loading code


### Endpoints and error codes

Review our [Test API specifications page](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders-test-support/1.0) to see the endpoint and possible error codes.

### Test scenario details

|Code |Identifier | Details|
|---|------|-------------|
|GB015B|Syntax identifier|UNOC|
| |Syntax version Number| 3|
| |Message sender|Please use your own unique identifier e.g EORI (DO NOT USE THE ONES SUPPLIED BELOW) |
| |Message recipient| NCTS|
| |Date of preparation|_Current date (ccyymmdd)_|
| |Time of preparation |_Current time (hhmm)_|
| |Interchange Control Reference| _Unique Reference Number_|
| |Application Reference|NCTS |
| |Message identification| 1|
| |Message type |GB015B|
|HEA |Reference number |TRATESTDEC1 _yymmddhhmm_|
| |Type of Declaration| T1|
| |Country of destination code|IT|
| |Authorised location of goods|_954131533-GB60DEP_|
| |Country of dispatch/export code| GB|
| |Identity of means of transport at departure|NC15REG|
| |Nationality of means of transport at departure|GB|
| |Containerised indicator|0 |
| |NCTS accompanying doc language code| EN|
| |Total Number of items |1|
| |Total number of packages| 10|
| |Total gross mass|1000 |
| |Declaration date| _Current Date (ccyymmdd)_|
| |Declaration place |Dover|
| |Language code |EN|
| |Specific circumstance indicator| C|
| |Commerical reference number|HQDOV001 |
| |Security| 1|
| |Place of unloading code |MONOPOLI001|



### Principle
|Code|Identifier | Details|
|---|------|-------------|
|PC1|Trader Name|NCTS UK TEST LAB HMCE|
| |Trader Street and Number| 11TH FLOOR, ALEX HOUSE, VICTORIA AV|
| |Trader Postal Code|SS99 1AA |
| |Trader Postal Code|SOUTHEND-ON-SEA, ESSEX |
| |Trader Country Code| GB|
| |Trader Name and Address Language Code|EN|
| |Trader EORI |GB954131533000|

### Consignor
|Code |Identifier | Details|
|---|------|-------------|
| CO1|Trader Name|NCTS UK TEST LAB HMCE|
| |Trader Street and Number| 11TH FLOOR, ALEX HOUSE, VICTORIA AV|
| |Trader Postal Code|SS99 1AA |
| |Trader Postal Code|SOUTHEND-ON-SEA, ESSEX |
| |Trader Country Code| GB|
| |Trader Name and Address Language Code|EN|
| |Trader EORI |GB954131533000|

### Consignee
|Code |Identifier | Details|
|---|------|-------------|
| CE1|Trader name|NCTS UK TEST LAB HMCE|
| |Trader street and number| ITALIAN OFFICE|
| |Trader postal code|IT99 1IT |
| |Trader city| MILAN|
| |Trader country code | IT|
| |Trader Name and Address Language Code|EN|
| |Trader EORI |IT11ITALIANC11|

### Office of departure
|Code|Identifier | Details|
|---|------|-------------|
|EPT |Reference Number|GB000060|

### Office of transit
|Code|Identifier | Details|
|---|------|-------------|
|RNS |Reference Number|CH001252|
| |Arrival time|2 days from current date (ccyymmdd) current time (hhmm)|

### Office of destination
|Code|Identifier | Details|
|---|------|-------------|
|EST |Reference Number|IT018105|

### Control result
|Code|Identifier | Details|
|---|------|-------------|
|ERS |Control result code|A3|
| |Date Limit|8 days from current date |

### Seals information
|Code|Identifier | Details|
|---|------|-------------|
|SLI |Seals number|1|
| |Seals ID|NCTS001|

#

### XML Definitions

|Code|Definition |
|---|------|
|X|X|
|X|X|
|X|X|
|X|X|
|X|X|
|X|X|
|X|X|
|X|X|


### Review the XSD File

[ CC015B XSD File](https://github.com/hmrc/common-transit-convention-traders/blob/master/conf/xsd/cc015b.xsd)

### Sample XML

```
 CC015B xmlns="http://ncts.hmce.gov.uk/CC015B.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<SynIdeMES1>UNOC</SynIdeMES1>
<SynVerNumMES2>3</SynVerNumMES2>
<MesSenMES3>SYST17B-NCTS_EU_EXIT</MesSenMES3>
<MesRecMES6>NCTS</MesRecMES6>
<DatOfPreMES9>20190912</DatOfPreMES9>
<TimOfPreMES10>1222</TimOfPreMES10>
<IntConRefMES11>WE190912102530</IntConRefMES11>
<AppRefMES14>NCTS</AppRefMES14>
<TesIndMES18>0</TesIndMES18>
<MesIdeMES19>1</MesIdeMES19>
<MesTypMES20>GB015B</MesTypMES20>
<HEAHEA>
<RefNumHEA4>01CTC201909121215</RefNumHEA4>
<TypOfDecHEA24>T2</TypOfDecHEA24>
<CouOfDesCodHEA30>IT</CouOfDesCodHEA30>
<AgrLocOfGooCodHEA38 xsi:nil="true"/>
<AgrLocOfGooHEA39 xsi:nil="true"/>
<AgrLocOfGooHEA39LNG>EN</AgrLocOfGooHEA39LNG>
<AutLocOfGooCodHEA41 xsi:nil="true"/>
<PlaOfLoaCodHEA46>DOVER</PlaOfLoaCodHEA46>
<CouOfDisCodHEA55>GB</CouOfDisCodHEA55>
<CusSubPlaHEA66 xsi:nil="true"/>
<InlTraModHEA75>20</InlTraModHEA75>
<IdeOfMeaOfTraAtDHEA78>EU_EXIT</IdeOfMeaOfTraAtDHEA78>
<IdeOfMeaOfTraAtDHEA78LNG>EN</IdeOfMeaOfTraAtDHEA78LNG>
<IdeOfMeaOfTraCroHEA85>EU_EXIT</IdeOfMeaOfTraCroHEA85>
<IdeOfMeaOfTraCroHEA85LNG>EN</IdeOfMeaOfTraCroHEA85LNG>
<ConIndHEA96>0</ConIndHEA96>
<DiaLanIndAtDepHEA254>EN</DiaLanIndAtDepHEA254>
<NCTSAccDocHEA601LNG>EN</NCTSAccDocHEA601LNG>
<TotNumOfIteHEA305>1</TotNumOfIteHEA305>
<TotNumOfPacHEA306>1</TotNumOfPacHEA306>
<TotGroMasHEA307>1000</TotGroMasHEA307>
<DecDatHEA383>20190912</DecDatHEA383>
<DecPlaHEA394>DOVER</DecPlaHEA394>
<DecPlaHEA394LNG>EN</DecPlaHEA394LNG>
</HEAHEA>
<TRAPRIPC1>
<NamPC17>CITY WATCH SHIPPING</NamPC17>
<StrAndNumPC122>125 Psuedopolis Yard</StrAndNumPC122>
<PosCodPC123>SS99 1AA</PosCodPC123>
<CitPC124>Ank-Morpork</CitPC124>
<CouPC125>GB</CouPC125>
<NADLNGPC>EN</NADLNGPC>
<TINPC159>GB652420267000</TINPC159>
</TRAPRIPC1>
<TRACONCO1>
<NamCO17>QUIRM ENGINEERING</NamCO17>
<StrAndNumCO122>125 Psuedopolis Yard</StrAndNumCO122>
<PosCodCO123>SS99 1AA</PosCodCO123>
<CitCO124>Ank-Morpork</CitCO124>
<CouCO125>GB</CouCO125>
<TINCO159>GB602070107000</TINCO159>
</TRACONCO1>
<TRACONCE1>
<NamCE17>DROFL POTTERY</NamCE17>
<StrAndNumCE122>125 Psuedopolis Yard</StrAndNumCE122>
<PosCodCE123>SS99 1AA</PosCodCE123>
<CitCE124>Ank-Morpork</CitCE124>
<CouCE125>GB</CouCE125>
<NADLNGCE>EN</NADLNGCE>
<TINCE159>GB658120050000</TINCE159>
</TRACONCE1>
<CUSOFFDEPEPT>
<RefNumEPT1>GB000060</RefNumEPT1>
</CUSOFFDEPEPT>
<CUSOFFTRARNS>
<RefNumRNS1>FR001260</RefNumRNS1>
<ArrTimTRACUS085>201909160100</ArrTimTRACUS085>
</CUSOFFTRARNS>
<CUSOFFDESEST>
<RefNumEST1>IT021100</RefNumEST1>
</CUSOFFDESEST>
<SEAINFSLI>
<SeaNumSLI2>1</SeaNumSLI2>
<SEAIDSID>
<SeaIdeSID1>Seal001</SeaIdeSID1>
<SeaIdeSID1LNG>EN</SeaIdeSID1LNG>
</SEAIDSID>
</SEAINFSLI>
<GUAGUA>
<GuaTypGUA1>3</GuaTypGUA1>
<GUAREFREF>
<GuaRefNumGRNREF1 xsi:nil="true"/>
<OthGuaRefREF4>EU_EXIT</OthGuaRefREF4>
<AccCodREF6 xsi:nil="true"/>
</GUAREFREF>
</GUAGUA>
<GOOITEGDS>
<IteNumGDS7>1</IteNumGDS7>
<ComCodTarCodGDS10 xsi:nil="true"/>
<DecTypGDS15 xsi:nil="true"/>
<GooDesGDS23>Flowers</GooDesGDS23>
<GooDesGDS23LNG>EN</GooDesGDS23LNG>
<GroMasGDS46>1000</GroMasGDS46>
<NetMasGDS48>999</NetMasGDS48>
<CouOfDesGDS59 xsi:nil="true"/>
<PREADMREFAR2>
<PreDocTypAR21>T2</PreDocTypAR21>
<PreDocRefAR26>EU_EXIT-T2</PreDocRefAR26>
<PreDocRefLNG>EN</PreDocRefLNG>
<ComOfInfAR29 xsi:nil="true"/>
<ComOfInfAR29LNG>EN</ComOfInfAR29LNG>
</PREADMREFAR2>
<PRODOCDC2>
<DocTypDC21>720</DocTypDC21>
<DocRefDC23>EU_EXIT</DocRefDC23>
<DocRefDCLNG>EN</DocRefDCLNG>
<ComOfInfDC25 xsi:nil="true"/>
<ComOfInfDC25LNG>EN</ComOfInfDC25LNG>
</PRODOCDC2>
<PACGS2>
<MarNumOfPacGS21>Bloomingales</MarNumOfPacGS21>
<MarNumOfPacGS21LNG>EN</MarNumOfPacGS21LNG>
<KinOfPacGS23>BX</KinOfPacGS23>
<NumOfPacGS24>1</NumOfPacGS24>
</PACGS2>
</GOOITEGDS>
</CC015B>
```

## Declaration rejected IE016

### [See IE016 diagram](diagrams.html#declaration-rejection-diagram-ie016)


### Endpoints and error codes

Review our [Test API specifications page](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders-test-support/1.0) to see the endpoint and possible error codes.

### Test Scenario details


|Code |Identifier | Details|
|---|------|-------------|
|GB016B|Syntax identifier|UNOC|
| |Syntax version Number| 3|
| |Message sender|NTA.GB|
| |Message recipient| _As ‘Message Sender’ from the IE015_|
| |Date of preparation|_Current date (ccyymmdd)_|
| |Time of preparation |_Current time (hhmm)_|
| |Interchange Control Reference| _Unique Reference Number_|
| |Application Reference|NCTS |
| | Test indicator| 0|
| |Message identification| _Same as Interchange Control Reference_|
| |Message type |GB016A|
|HEA |Reference number |_Reference Number from IE015_|
| |Type of Declaration| T1|
| |Declaration rejection date|_Current date(ccyymmdd)_|
| |Declaration rejection reason|The IE015 message received was invalid|

### Functional error

|Code |Identifier | Details|
|---|------|-------------|
|ER1|Error type|15|
| |Error pointer|HEA place of loading code|
| |Error reason|C191|


### Sample XML

```
 CC015B xmlns="http://ncts.hmce.gov.uk/CC015B.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<SynIdeMES1>UNOC</SynIdeMES1>
<SynVerNumMES2>3</SynVerNumMES2>
<MesSenMES3>SYST17B-NCTS_EU_EXIT</MesSenMES3>
<MesRecMES6>NCTS</MesRecMES6>
<DatOfPreMES9>20190912</DatOfPreMES9>
<TimOfPreMES10>1222</TimOfPreMES10>
<IntConRefMES11>WE190912102530</IntConRefMES11>
<AppRefMES14>NCTS</AppRefMES14>
<TesIndMES18>0</TesIndMES18>
<MesIdeMES19>1</MesIdeMES19>
<MesTypMES20>GB015B</MesTypMES20>
<HEAHEA>
<RefNumHEA4>01CTC201909121215</RefNumHEA4>
<TypOfDecHEA24>T2</TypOfDecHEA24>
<CouOfDesCodHEA30>IT</CouOfDesCodHEA30>
<AgrLocOfGooCodHEA38 xsi:nil="true"/>
<AgrLocOfGooHEA39 xsi:nil="true"/>
<AgrLocOfGooHEA39LNG>EN</AgrLocOfGooHEA39LNG>
<AutLocOfGooCodHEA41 xsi:nil="true"/>
<PlaOfLoaCodHEA46>DOVER</PlaOfLoaCodHEA46>
<CouOfDisCodHEA55>GB</CouOfDisCodHEA55>
<CusSubPlaHEA66 xsi:nil="true"/>
<InlTraModHEA75>20</InlTraModHEA75>
<IdeOfMeaOfTraAtDHEA78>EU_EXIT</IdeOfMeaOfTraAtDHEA78>
<IdeOfMeaOfTraAtDHEA78LNG>EN</IdeOfMeaOfTraAtDHEA78LNG>
<IdeOfMeaOfTraCroHEA85>EU_EXIT</IdeOfMeaOfTraCroHEA85>
<IdeOfMeaOfTraCroHEA85LNG>EN</IdeOfMeaOfTraCroHEA85LNG>
<ConIndHEA96>0</ConIndHEA96>
<DiaLanIndAtDepHEA254>EN</DiaLanIndAtDepHEA254>
<NCTSAccDocHEA601LNG>EN</NCTSAccDocHEA601LNG>
<TotNumOfIteHEA305>1</TotNumOfIteHEA305>
<TotNumOfPacHEA306>1</TotNumOfPacHEA306>
<TotGroMasHEA307>1000</TotGroMasHEA307>
<DecDatHEA383>20190912</DecDatHEA383>
<DecPlaHEA394>DOVER</DecPlaHEA394>
<DecPlaHEA394LNG>EN</DecPlaHEA394LNG>
</HEAHEA>
<TRAPRIPC1>
<NamPC17>CITY WATCH SHIPPING</NamPC17>
<StrAndNumPC122>125 Psuedopolis Yard</StrAndNumPC122>
<PosCodPC123>SS99 1AA</PosCodPC123>
<CitPC124>Ank-Morpork</CitPC124>
<CouPC125>GB</CouPC125>
<NADLNGPC>EN</NADLNGPC>
<TINPC159>GB652420267000</TINPC159>
</TRAPRIPC1>
<TRACONCO1>
<NamCO17>QUIRM ENGINEERING</NamCO17>
<StrAndNumCO122>125 Psuedopolis Yard</StrAndNumCO122>
<PosCodCO123>SS99 1AA</PosCodCO123>
<CitCO124>Ank-Morpork</CitCO124>
<CouCO125>GB</CouCO125>
<TINCO159>GB602070107000</TINCO159>
</TRACONCO1>
<TRACONCE1>
<NamCE17>DROFL POTTERY</NamCE17>
<StrAndNumCE122>125 Psuedopolis Yard</StrAndNumCE122>
<PosCodCE123>SS99 1AA</PosCodCE123>
<CitCE124>Ank-Morpork</CitCE124>
<CouCE125>GB</CouCE125>
<NADLNGCE>EN</NADLNGCE>
<TINCE159>GB658120050000</TINCE159>
</TRACONCE1>
<CUSOFFDEPEPT>
<RefNumEPT1>GB000060</RefNumEPT1>
</CUSOFFDEPEPT>
<CUSOFFTRARNS>
<RefNumRNS1>FR001260</RefNumRNS1>
<ArrTimTRACUS085>201909160100</ArrTimTRACUS085>
</CUSOFFTRARNS>
<CUSOFFDESEST>
<RefNumEST1>IT021100</RefNumEST1>
</CUSOFFDESEST>
<SEAINFSLI>
<SeaNumSLI2>1</SeaNumSLI2>
<SEAIDSID>
<SeaIdeSID1>Seal001</SeaIdeSID1>
<SeaIdeSID1LNG>EN</SeaIdeSID1LNG>
</SEAIDSID>
</SEAINFSLI>
<GUAGUA>
<GuaTypGUA1>3</GuaTypGUA1>
<GUAREFREF>
<GuaRefNumGRNREF1 xsi:nil="true"/>
<OthGuaRefREF4>EU_EXIT</OthGuaRefREF4>
<AccCodREF6 xsi:nil="true"/>
</GUAREFREF>
</GUAGUA>
<GOOITEGDS>
<IteNumGDS7>1</IteNumGDS7>
<ComCodTarCodGDS10 xsi:nil="true"/>
<DecTypGDS15 xsi:nil="true"/>
<GooDesGDS23>Flowers</GooDesGDS23>
<GooDesGDS23LNG>EN</GooDesGDS23LNG>
<GroMasGDS46>1000</GroMasGDS46>
<NetMasGDS48>999</NetMasGDS48>
<CouOfDesGDS59 xsi:nil="true"/>
<PREADMREFAR2>
<PreDocTypAR21>T2</PreDocTypAR21>
<PreDocRefAR26>EU_EXIT-T2</PreDocRefAR26>
<PreDocRefLNG>EN</PreDocRefLNG>
<ComOfInfAR29 xsi:nil="true"/>
<ComOfInfAR29LNG>EN</ComOfInfAR29LNG>
</PREADMREFAR2>
<PRODOCDC2>
<DocTypDC21>720</DocTypDC21>
<DocRefDC23>EU_EXIT</DocRefDC23>
<DocRefDCLNG>EN</DocRefDCLNG>
<ComOfInfDC25 xsi:nil="true"/>
<ComOfInfDC25LNG>EN</ComOfInfDC25LNG>
</PRODOCDC2>
<PACGS2>
<MarNumOfPacGS21>Bloomingales</MarNumOfPacGS21>
<MarNumOfPacGS21LNG>EN</MarNumOfPacGS21LNG>
<KinOfPacGS23>BX</KinOfPacGS23>
<NumOfPacGS24>1</NumOfPacGS24>
</PACGS2>
</GOOITEGDS>
</CC015B>
```
