
![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Customer API 

#### Release version 1.0

## About the Customer API 

The customer API provides general information about a customer. It is one of eight APIs that together make up the customer services suite. 

>**NOTE:** The Customer API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation

* View and download the [Customer API YAML](Customer%202021-09-14.yaml)
* [Download the Customer API build pack](Build%20pack%20-%20Customer%20API.pdf) to view data definitions of each operation and response status code definitions
* [Sample Messages](#Sample-Messages) to a list of successful and errored JSON request and response messages 	
* [View API Reference and URL endpoints](#Customer-API-REST-Reference)	

## Environment information

* [Mock environment information - emulated service URL, scenarios mindmap and test data](#mock-environment-information)

## Supporting services

* Identity and access - view: [How to integrate, M2M JWT, OAuth  requests and responses message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)

---


<a name="Sample-Messages"></a>
## Sample messages

| Service | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | :--: | -- | -- | -- | 
| customer | `200` | Successful Request | [Request](sample%20messages/POST_200_customer_request.json) | [Response](sample%20messages/POST_200_customer_response.json) | 
| customer | `400` | Non-existent IRD number | [Request](sample%20messages/POST_400_customer_CST404_non-existent_IRD_number_request.json) | [Response](sample%20messages/POST_400_customer_CST404_non-existent_IRD_number_response.json) |
| customer | `400` | Hyphenated IRD number | [Request](sample%20messages/POST_400_customer_EV1100_hyphenated_IRD_number_request.json) | [Response](sample%20messages/POST_400_customer_EV1100_hyphenated_IRD_number_response.json) |
| customer | `400` | Missing Customer ID Type | [Request](sample%20messages/POST_400_customer_EV1100_missing_CustomerIDType_request.json) | [Response](sample%20messages/POST_400_customer_EV1100_missing_CustomerIDType_response.json) |


<a name="Customer-API-REST-Reference"></a>
## Customer API REST Reference

| Environment | Scheme Authority | Mutual TLS (mTLS) authentication |
| --- | --- | :---: |
| Mock (DPS)| `https://customerservices.test.services.ird.govt.nz`| no |
| Production (PROD) | `https://services.ird.govt.nz:4046`| yes |

#### Customer API - `{Scheme Authority}/gateway/customer/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| customer | `POST` | Returns the information of an identified customer |
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 

> The `status` service might not be available in the mock environment.

<a name="mock-environment-information"></a>
## Mock environment information
---

### Mock emulated service URL
* Landing Page https://customerservices.test.services.ird.govt.nz

### Customer mock scenarios mindmap

[View larger image](../images/Customer%20API%20Mock%20Service.png)
![Mock Scenarios](../images/Customer%20API%20Mock%20Service.png)

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
* Download [Test Scenarios Report Template](Customer%20API%20-%20Test%20Report%20Template%20v1.1.docx)




