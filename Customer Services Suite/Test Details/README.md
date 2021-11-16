
![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Customer Services Suite Test Details
#### Release version 1.0 

## Test accounts and IRD numbers
|Persona|IRD number<br/> ("CustomerIDType": "IRD")|Customer ID<br/> ("CustomerIDType": "CST")|AccountID<br/> ("AccountIDType": "ACC")|AddressID|ContactID|NameID|Phone ID||Numeric Identifiers<br/>(These identifiers work against any persona unless specified)||||
|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|INDIVIDUAL|132243158||132243158FAM005<br/>132243158GST004<br/>132243158INC003<br/>132243158DSB006 (For error BNK102 only)<br/>132243158FBT005 (For errors BNK101, CNT101 and NAM101) <br/>132243158KSS004 (For error ACT100)||||||AddressID|ContactID|NameID|Phone ID|
|NON_INDIVIDUAL|069096409||069096409EMP003<br/>069096409INC002||||||5342356299, <br/>5342123299, 1004723453056, 1004722686772,<br/>1004733565010, 5341463520, 1004732460550, 1004785546432|1295148032, 1578864256|1004723443833, 1004723099665, 1004723362815, 1016545454547|9004732142020, 1004734460042|
|ANOTHER_CUSTOMER|139369673||139369673AIL023<br/>139369673INC003<br/>139369673REB001||||||||||
|CUSTOMER_WITH_CST_ID||1512150403|||||||||||
|IRD_FAILED_CHECK_DIGIT|123456789||||||||||||
|EV1022_CUSTOMER|102210221||102210221INC002|5342123299, 1004732460550, 1004785546432|1320547545|1016545454547|9005454545845||||||

## Error Code & Error Messages
|||||Generic Errors|||||||API Specific Errors|||||||||||| |||
|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|||||ACT100|CST404|EV1020|EV1021|EV1022|EV1100 |EV2234|ADR100|ADR101|ADR102|ADR103|BNK100|BNK101|BNK102|CNT101|CNT102|CNT103|NAM100|NAM101|BIC101|BIC102|BIC103|
|||||<br/>This account type is not eligible to be used in this service.|<br/>A record could not be located for the given identifier.|<br/>Authentication failure means the token (JWT or OAuth) provided is not valid|<br/>No OAuth or JWT token is present as an HTTP header|<br/>Access is not permitted for the requester to perform this operation for the submitted identifier| <br/>Invalid input parameters|<br/>IR number failed check digit|	An address of this type cannot be deleted. Please update instead|There is an existing address of this type|The address provided is invalid|The DPID provided is invalid|<br/>The bank account provided is invalid|<br/>The account provided does not have an existing bank account associated|<br/>There is no physical address for the customer or account for the provided country|<br/>There is an existing contact of this type|<br/>The phone number provided is invalid|<br/>There must be between 1 and 5 phone numbers on a contact|A name of this type cannot be deleted. Please update instead.|<br/>There is an existing name of this type||||
|**API**|**SERVICE**|**METHOD**|**Record Level Affected**|||||||
|Customer|Customer|POST|Customer||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|Use Persona IRD_FAILED_CHECK_DIGIT||||
|||||||||||||||||||||||||||
|Account|List|POST|Customer||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|Use Persona IRD_FAILED_CHECK_DIGIT|||||||
|Account|Account|POST|Account|When account type is not in eligible list (e.g. 132243158KSS004,<br/>139376056KSS004)|Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|||||||||||||||||
|||||||||||||||||||||||||||
|Period|List|POST|Account|When account type is not in eligible list (e.g. 132243158KSS004,<br/>139376056KSS004)|Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|||||||||||||||||
|||||||||||||||||||||||||||
|Address|Address|POST|Customer & Account|When account type is not in eligible list (e.g. 132243158KSS004,<br/>139376056KSS004)|Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|Use Persona IRD_FAILED_CHECK_DIGIT||With CustomerID in the request as well as Type = "LOC"|Using invalid Unit type in the request or<br/>Urbanisation is missing when Country = "AU" or<br/>State is missing for Country = "AU" or "CA" or "US"<br/>Also when unitType is invalid|Using a DPID that is NOT between 55 and 7449050 or 82794 or 12345||||||||||||
|Address|Address|PUT|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|AddressID:<br/>1004732460550, 1004785546432|When request does not match yaml file||||Using invalid Unit type in the request or<br/>Urbanisation is missing when Country = "AU" or<br/>State is missing for Country = "AU" or "CA" or "US"<br/>Also when unitType is invalid|Using a DPID that is NOT between 55 and 7449050 or 82794 or 12345||||||||||||
|Address|Address|DELETE|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|AddressID:<br/>1004732460550, 1004785546432|When request does not match yaml file||5342356299 or 5341463520|||||||||||||||
|||||||||||||||||||||||||||
|Contact|Contact|POST|Customer & Account|When account type is not in eligible list (e.g. 132243158KSS004)|Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|Use Persona IRD_FAILED_CHECK_DIGIT||||||||AccountID: 132243158FBT005|with invalid phone number (e.g. non-numeric characters for AreaCode)|with 0 or 6 phone numbers in the request||||||
|Contact|Contact|PUT|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER<br/>ContactID: 1320547545|When request does not match yaml file|||||||||||Not emulated||||||
|Contact|Contact|DELETE|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER<br/>ContactID: 1320547545|When request does not match yaml file|||||||||||Not emulated||||||
|Contact|Phone|POST|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file||||||||||with invalid phone number (e.g. non-numeric characters for AreaCode)|Not emulated||||||
|Contact|Phone|PUT|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER<br/>PhoneID: 9005454545845|When request does not match yaml file||||||||||with invalid phone number (e.g. non-numeric characters for AreaCode)|Not emulated||||||
|Contact|Phone|DELETE|Customer & Account||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER<br/>PhoneID: 9005454545845|When request does not match yaml file|||||||||||Not emulated||||||
|||||||||||||||||||||||||||
|Bank|Bank|POST|Account|When account type is not in eligible list (e.g. KSS)|Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER<br/>(Account only)|When request does not match yaml file||||||Using non-digit caracters or using 00 0000 00000000 0000||AccountID: 132243158DSB006|||||||||
|Bank|Bank|DELETE|Account|When account type is not in eligible list (e.g. KSS)|Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER<br/>(Account only)|When request does not match yaml file|||||||AccountID: 132243158FBT005||||||||||
|||||||||||||||||||||||||||
|Name|Name|POST|Customer||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|Use persona EV1022_CUSTOMER|When request does not match yaml file|Use Persona IRD_FAILED_CHECK_DIGIT||||||||||||CustomerIRD: <br/>139390032||||
|Name|Name|PUT|Customer||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|NameID:<br/>1016545454547|When request does not match yaml file|||||||||||||||||
|Name|Name|DELETE|Customer||Default response (using ID that is not displayed in this page)|Using invalid<br/> token|Header Authorization<br/> is missing|NameID:<br/>1016545454547|When request does not match yaml file||||||||||||NameID:<br/>1004723443833|||||
|||||||||||||||||||||||||||
|Bic|Bic|POST|Customer| |Default response (using ID that is not displayed in this page)|Using invalid token|Header Authorization is missing|Use persona EV1022_CUSTOMER or CustomerID: 139616936|When request does not match yaml file|IR number failed check digit| | | | | | | | | | | | | |use future commence date||||
|Bic|Bic|DELETE|Customer| |Default response (using ID that is not displayed in this page)|Using invalid token|Header Authorization is missing|Use persona EV1022_CUSTOMER or CustomerID: 139616936|When request does not match yaml file|IR number failed check digit| | | | | | | | | | | | |BICCode: C249910||use future cease date||
																											

