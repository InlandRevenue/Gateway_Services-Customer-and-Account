
![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Bank API 

#### Release version 1.0

## About the Bank API 

The bank account API enables the creating and deleting of the refund bank account for an identified customer’s account. It is one of eight APIs that together make up the customer services suite.

>**NOTE:** The Bank API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation
* View and download the [Bank API YAML](Bank%202021-09-14.yaml)
* [Download the Bank API build pack](Build%20pack%20-%20Bank%20API.pdf) to view data definitions of each operation and response status code definitions
* [Sample Messages](#Sample-Messages) to a list of successful and errored JSON request messages 
* [View API Reference and URL endpoints](#Bank-API-REST-Reference)	

## Environment information
* [Mock environment information - emulated service URL, scenarios mindmap and test data](#mock-environment-information)

## Supporting services
* Service: Identity and access - view: [How to integrate, M2M JWT, OAuth requests and responses message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)
* [Account API](../Account%20API)
---

<a name="Sample-Messages"></a>
### Sample messages

| Service | HTTP request types | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | -- | :--: | -- | -- | -- | 
| bank | DELETE | `200` | Delete bank account | [Request](sample%20messages/DELETE_200_Delete_bank_request.json) | Validate HTTP Status Code | 
| bank | DELETE | `400` | The account provided does not have an existing bank account associated | [Request](sample%20messages/DELETE_400_Delete_bank_account_provided_does_not_have_an_existing_bank_account.json) | Validate HTTP Status Code  | 
| bank | POST | `200` | Create international bank account | [Request](sample%20messages/POST_200_bank_Create_international_bank_account_request.json) | Validate HTTP Status Code  | 
| bank | POST | `200` | Create NZ bank account | [Request](sample%20messages/POST_200_bank_Create_NZ_bank_account_request.json) | Validate HTTP Status Code  | 
| bank | POST | `200` | Create NZ credit union bank account | [Request](sample%20messages/POST_200_bank_Create_NZ_credit_union_bank_account.json) | Validate HTTP Status Code  | 
| bank | POST | `400` | There is no physical address for the customer or account for the provided country | [Request](sample%20messages/POST_400_bank_no_physical_address_for_the_customer_request.json) | Validate HTTP Status Code  | 


<a name="Bank-API-REST-Reference"></a>
## Bank API REST Reference and URL endpoints

| Environment | Scheme Authority | Mutual TLS (mTLS) authentication |
| --- | --- | :---: |
| Mock (DPS)| `https://customerservices.test.services.ird.govt.nz`| no |
| Production (PROD) | `https://services.ird.govt.nz:4046`| yes |

#### Bank API - `{Scheme Authority}/gateway/bank/{Service}`
| Service | HTTP request types | Description | 
| -- | :--: | -- | 
| bank |  `DELETE` | Deletes the refund bank account from the identified customer account |
| bank |  `POST` | Adds a refund bank account to the identified customer account if there is not already a refund bank account on the customer account<br/>Or<br/>Replaces an existing refund bank account on the identified customer account  |
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 

> The `status` service might not be available in the mock environment.

<a name="mock-environment-information"></a>
## Mock environment information

### Mock emulated service URL
* Landing Page https://customerservices.test.services.ird.govt.nz

### Bank mock scenarios mindmap

[View larger image](../images/Bank%20API%20Mock%20Service.png)
![Mock Scenarios](../images/Bank%20API%20Mock%20Service.png)

### Mock environment authentication
   * Consumers of this mock service must be authenticated.
   * Access delegation/restriction is not emulated, and any authenticated user has access to the test data.
   * Authentication is provided using one of two methods:
     1. OAuth
        * OAuth token issued by the mock OAuth service. Any valid token issued by the mock OAuth service can be used to access this service.
        * Please consult the [mock OAuth service documentation](https://oauth.test.services.ird.govt.nz/) for further details about the authentication process.
        * The OAuth token should be provided in the 'Authorization' request header as follows:
        ```
        Authorization: Bearer {OAuthAccessToken}
        ```
     2. JWT
        * Alternatively a self-issued JWT may be used to access the service.
        * Please consult the build pack for information on the token structure.
        * The mock service does not validate the following JWT attributes:
            * "sub" field
            * "iss" field
            * token signature
        * The JWT should be provided in the 'Authorization' request header as follows (note the 'Bearer' prefix is omitted):
        ```
        Authorization: {JWT}
        ```
		
### Test mock data
* [Mock Test Data](../Test%20Details/) 		
		
### Test scenarios report template

- [Download Test Scenarios report template](Bank%20API%20-%20Test%20Report%20Template_v1.2.docx) 



