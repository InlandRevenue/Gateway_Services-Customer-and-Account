
![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Period API 

#### Release version 1.0

## About the Period API

The period API provides information about one or more periods for an identified customer account. It is one of eight APIs that together make up the customer services suite. 

>**NOTE:** The Period API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation

* View and download the [Period API YAML](Period%202021-10-28.yaml)
* [Download the Period API build pack](Build%20pack%20-%20Period%20API.pdf) to view data definitions of each operation and response status code definitions
* [Sample Messages](#Sample-Messages) to a list of successful and errored JSON request and response messages 
* [View API Reference and URL endpoints](#Period-API-REST-Reference)
	
## Environment information

* [Mock environment information - emulated service, scenarios mindmap and test data](#mock-environment-information)
	

## Supporting services

* Identity and access - view: [How to integrate, M2M JWT, OAuth requests and responses message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)
* [Account API](../Account%20API)

---

<a name="Sample-Messages"></a>
### Sample messages

| Service | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | :--: | -- | -- | -- | 
| list | `200` | Non-INC_account | [Request](sample%20messages/POST_200_list_non-INC_account_request.json) | [Response](sample%20messages/POST_200_list_non-INC_account_response.json) | 
| list | `200` | Specific_INC period details | [Request](sample%20messages/POST_200_list_specific_INC_period_details_response.json) | [Response](sample%20messages/POST_200_list_specific_INC_period_details_response.json) | 
| list | `400` | EV1022 Access not permitted | [Request](sample%20messages/POST_400_list_EV1022_access_not_permitted_request.json) | [Response](sample%20messages/POST_400_list_EV1022_access_not_permitted_response.json) | 
| list | `400` | EV1100 Invalid From Date | [Request](sample%20messages/POST_400_list_EV1100_invalid_From_Date_request.json) | [Response](sample%20messages/POST_400_list_EV1100_invalid_From_Date_response.json) | 


<a name="Period-API-REST-Reference"></a>
### URL Endpoints and API Reference

| Environment | Scheme Authority | mutual TLS |
| --- | --- | :---: |
| Mock (DPS)| `https://customerservices.test.services.ird.govt.nz`| no |
| Production (PROD) | `https://services.ird.govt.nz:4046`| yes |

<a Period="API-REST-Reference"></a>
#### Period API - `{Scheme Authority}/gateway/period/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| list | `POST` | Returns the information of periods for an identified customer account | 
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 

> The `status` service might not be available in the mock environment. 



<a Period="mock-environment-information"></a>
## Mock environment information

### Mock emulated service URL landing page 
* https://customerservices.test.services.ird.govt.nz

### Period mock scenarios mindmap

[View larger image](../images/Period%20API%20Mock%20Service.png)
![Mock Scenarios](../images/Period%20API%20Mock%20Service.png)


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

* Download [Test Scenarios Report Template](Period%20List%20API%20-%20Test%20Report%20Template_v1.2.docx)

