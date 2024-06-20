
![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Bill Service
---
#### Release version 1.0 


## About the service
* This service is an application programming interface (API) that external applications can call in real-time to retrieve information for a particular customer bill item. The response also includes provisional tax method details and history associated to the account to which the bill item belongs.
* The objective of this API is to allow transaction data services (TDS) software providers to query information that was formerly available in the Tax Agent Web Services (TAWS) data feed.

## Key documentation
---
- YAML file
	- View and download the [Bill API YAML](Bill%202020-09-30.yaml)

- Build pack
	- [Download the Bill API build pack](Build%20pack%20-%20Bill%20API.pdf) to view data definitions of each operation and response status code definitions

- Message samples
	- [View message samples for requests and positive responses](#message-samples)

## Environment information
---
- [Mock environment information - emulated service URL, scenarios mind map and test data](#mock-environment-information)
	
- [Production environment information - URL endpoint](#Production-environment-information)	


## Supporting services
---
* Service: Identity and access - view: [How to integrate, OAuth requests and responses message samples and build pack]( https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)
* Service: [Transaction Data Services (TDS)](https://github.com/InlandRevenue/Gateway_Services-Transaction-data-services)


## Message Samples
---
- Sample JSON payload messages:
	- Request
		- [Request](Sample%20Files/Request.json)
	- Positive response
		- [Positive response](Sample%20Files/response_positive_response.json)


## Mock environment information
---
### Mock emulated service URL
|Description | URL|
|---|---|
| Landing Page | https://bill.test.services.ird.govt.nz|
| Service Path | https://bill.test.services.ird.govt.nz/gateway/bill/|
 
### Mock environment authentication
   * Consumers of this mock service must be authenticated.
   * Access delegation/restriction is not emulated, and any authenticated user has access to the test data.
   * Authentication is provided by an OAuth token issued by the mock OAuth service. Any valid token issued by the mock OAuth service can be used to access this service. Please consult the [mock OAuth service documentation](https://oauth.test.services.ird.govt.nz/) for further details about the authentication process.
   * The OAuth token should be provided in the 'Authorization' request header as follows:
   ```
   Authorization: Bearer {OAuthAccessToken}
   ```
### Bill mock scenarios mindmap

- [View larger image](images/BillAPI%20Mock%20Service%20Mindmap.png)
![Mock Scenarios](images/BillAPI%20Mock%20Service%20Mindmap.png)

### Test data

* This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses.
* Text in italics represents the name of a request header or field in the request body.

|  Scenario ID | Data | Http status | Response |
|--- | --- | --- | ---|
|MOCK-BILL-001 | *Bill.Id*: "1058166784" | 200 | Bill Item & Provisional Tax details|
|MOCK-BILL-002 | *Bill.Id*: "1411815424" | 200 | Bill Item & Provisional Tax details|
|MOCK-BILL-003 | *Bill.Id*: "865310720" | 200 | Bill Item & Provisional Tax details|
|MOCK-BILL-004 | *Bill.Id*: "282290176" | 200 | Bill Item & Provisional Tax details|
|MOCK-BILL-005 | *Bill.Id*: "1804888576" | 401 | EV1022 - Unauthorised delegation.|
|MOCK-BILL-008 | *Bill*: {"Invalid": true} | 400 | EV1100 - Incoming content contains invalid field names or field/value lengths exceeding 255 characters.|
|MOCK-BILL-009 | *Bill*: {} | 400 | EV2000 - Mandatory field - Bill.Id  - is missing|
|MOCK-BILL-010 | *Bill.Id*: "123" | 404 | ER5000 - No bill item found with input data|
|MOCK-BILL-011 | *Authorization*: "Bearer invalidtoken" | 401 | EV1020 - Authentication error|
|MOCK-BILL-012 | *Authorization*: (empty) | 401 | EV1021 - Missing OAuth in the HTTP header|

### Test scenarios report template

- [Download Test Scenarios report template](Bill%20API%20Service%20-%20Test%20Report%20Template.docx)


## Production environment information
---
### Production environment URL
| End point|  URL|
|--|--|
| Production | https://services.ird.govt.nz:4046/gateway/bill/ |

