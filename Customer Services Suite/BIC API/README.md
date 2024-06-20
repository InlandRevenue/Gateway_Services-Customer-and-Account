
![IRD logo](../../Images/IRlogo.gif)</br>
![Software Dev](../../Images/SoftwareDev.png)

# BIC API 

#### Release version 1.0

## About the BIC API 

The BIC API enables the adding / updating and ceasing of the BIC codes for an identified customer’s account. It is one of eight APIs that together make up the customer services suite.

>**NOTE:** The BIC API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation
* View and download the [BIC API YAML](BIC%202021-11-29.yaml)
* [Download the BIC API build pack](Build%20pack%20-%20BIC%20API.pdf) to view data definitions of each operation and response status code definitions
* [Sample Messages](#Sample-Messages) to a list of successful and errored JSON request messages 
* [View API Reference and URL endpoints](#BIC-API-REST-Reference)	

## Environment information
* [Mock environment information - emulated service URL, scenarios mindmap and test data](#mock-environment-information)

## Supporting services
* Service: Identity and access - view: [How to integrate, M2M JWT, OAuth requests and responses message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)
* [Customer API](../Customer%20API)
---

<a name="Sample-Messages"></a>
### Sample messages

| Service | HTTP request types | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | -- | :--: | -- | -- | -- | 
| bic | DELETE | 200 | Delete BIC request with CST ID | [Request](sample%20messages/DELETE_200_Delete_bic_request_with_CST_ID.json) | HTTP Status Code 200 | 
| bic | DELETE | 200 | Delete BIC request with IRD ID | [Request](sample%20messages/DELETE_200_Delete_bic_request_with_IRD_ID.json) | HTTP Status Code 200 |
| bic | DELETE | 400 | Delete non-existet BIC code request | [Request](sample%20messages/DELETE_400_bic_BIC101_delete_non-existet_biccode_request_payload.json) | [Response](sample%20messages/DELETE_400_bic_BIC101_delete_non-existet_biccode_response_payload.json) |
| bic | DELETE | 400 | Delete with future date request payload |[Request](sample%20messages/DELETE_400_bic_BIC103_delete_with_future_date_request_payload.json) | [Response](sample%20messages/DELETE_400_bic_BIC103_delete_with_future_date_response_payload.json) |
| bic | POST | 200 | Add BIC request with CST ID | [Request](sample%20messages/POST_200_Add_bic_request_with_CST_ID.json) | HTTP Status Code 200| 
| bic | POST | 200 | Add BIC request with IRD ID| [Request](sample%20messages/POST_200_Add_bic_request_with_IRD_ID.json) | HTTP Status Code 200 |
| bic | POST   | 400 | Add with future date request payload |[Request](sample%20messages/POST_400_bic_BIC102_add_with_future_date_request_payload.json) | [Response](sample%20messages/POST_400_bic_BIC102_add_with_future_date_response_payload.json) |



<a name="BIC-API-REST-Reference"></a>
## BIC API REST Reference and URL endpoints

| Environment | Scheme Authority | Mutual TLS (mTLS) authentication |
| --- | --- | :---: |
| Mock (DPS)| `https://customerservices.test.services.ird.govt.nz`| no |
| Production (PROD) | `https://services.ird.govt.nz:4046`| yes |

#### BIC API - `{Scheme Authority}/gateway/bic/{Service}`
| Service | HTTP request types | Description | 
| -- | :--: | -- | 
| bic |  `DELETE` | Ceases an existing BIC code on a customer |
| bic |  `POST` | Adds new or updates existing BIC code to customer  |
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 

> The `status` service might not be available in the mock or production environment.

<a name="mock-environment-information"></a>
## Mock environment information

### Mock emulated service URL
* Landing Page https://customerservices.test.services.ird.govt.nz

### BIC mock scenarios mindmap

[View larger image](../images/BIC%20API%20Mock.png)
![Mock Scenarios](../images/BIC%20API%20Mock.png)

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

- [Download Test Scenarios report template](BIC%20API%20-%20Test%20Report_v1.0.docx) 



