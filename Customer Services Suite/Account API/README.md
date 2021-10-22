![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Account API 

#### Release version 1.0

## About the Account API 

The account API provides either a list of accounts for an identified customer or information about a single customer account. It is one of eight APIs that together make up the customer services suite. An account represents a tax type (for example income tax) or a product (for example KiwiSaver). 

>**NOTE:** The Account API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation

* View and download the [Account API YAML](Account%202021-09-14.yaml)
* [Download the Account API build pack](Build%20pack%20-%20Account%20API.pdf) to view data definitions of each operation and response status code definitions
* [Sample Messages](#Sample-Messages) to a list of successful and errored JSON request and response messages 	
* [View API Reference and URL endpoints](#Account-API-REST-Reference)

## Environment information

* [Mock environment information - emulated service URL, scenarios mindmap and test data](#mock-environment-information)

## Supporting services

* Service: Identity and access - view: [How to integrate, OAuth, JWT requests and responses message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)

---

<a name="Sample-Messages"></a>
### Sample messages

| Service | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | :--: | -- | -- | -- | 
| account | `200` | Account with FAM account | [Request](sample%20messages/POST_200_Account_with_FAM_account_request.json) | [Response](sample%20messages/POST_200_Account_with_FAM_account_response.json) | 
| account | `200` | Account with GST account | [Request](sample%20messages/POST_200_Account_with_GST_account_request.json) | [Response](sample%20messages/POST_200_Account_with_GST_account_response.json) |
| account | `200` | Account with INC account | [Request](sample%20messages/POST_200_Account_with_INC_account_request.json) | [Response](sample%20messages/POST_200_Account_with_INC_account_response.json) |
| list | `200` | List Request| [Request](sample%20messages/POST_200_list_request.json) | [Response](sample%20messages/POST_200_list_response.json) |
| account | `400` | EV1022 error | [Request](sample%20messages/POST_400_account_EV1022_request.json) | [Response](sample%20messages/POST_400_account_EV1022_response.json) |
| list | `400` | EV1100 error | [Request](sample%20messages/POST_400_list_EV1100_request.json) | [Response](sample%20messages/POST_400_list_EV1100_response.json) |


<a name="Account-API-REST-Reference"></a>
## Account API REST Reference and URL Endpoints

| Environment | Scheme Authority | Mutual TLS (mTLS) authentication |
| --- | --- | :---: |
| Mock (DPS)| `https://customerservices.test.services.ird.govt.nz`| no |
| Production (PROD) | `https://services.ird.govt.nz:4046`| yes |

#### Account API - `{Scheme Authority}/gateway/Account/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| account | `POST` | Returns the information of an identified customer account | 
| list | `POST` | Returns a list of accounts for an identified customer | 
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 

> The `status` service might not be available in the mock environment. 

<a name="mock-environment-information"></a>
## Mock environment information

### Account API mock scenarios mindmap
- [View larger image](../images/Account%20API%20Mock%20Service.png)
![Mock Scenarios](../images/Account%20API%20Mock%20Service.png)





### Mock environment authentication
* Consumers of this mock service must be authenticated.
* Access delegation/restriction is not emulated, and any authenticated user has access to the test data.
* Authentication is provided using one of two methods:
 1. OAuth
	* OAuth token issued by the mock OAuth service. Any valid token issued by the mock OAuth service can be used to access this service.
	* Please consult the [mock OAuth service documentation](https://mock-oauth.ird.digitalpartner.services/) for further details about the authentication process.
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

- Download [Test Scenarios report template](Account%20API%20-%20Test%20Report%20Template_v1.1.docx)


