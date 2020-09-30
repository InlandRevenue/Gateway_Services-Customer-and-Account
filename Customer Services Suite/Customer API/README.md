
![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Customer API 

#### Release version 1.0

## About the Customer API 

Inland Revenue has a suite of digital services available for consumption by our service providers that supports efficient, electronic business interactions with Inland Revenue. 
The Customer API described in this build pack document provides current customer information as held by Inland Revenue. 

>**NOTE:** The Customer API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation
---
- YAML file
	- View and download the [Customer API YAML](Customer%202020-09-30.yaml)

- Build pack 
	- [Download the Customer API build pack](Build%20pack%20-%20Customer%20API.pdf) to view data definitions of each operation and response status code definitions
	
- Sample Messages
    - [Sample Messages](#Sample-Messages) to a list of successfull and errored JSON request and response messages 	
	
- API Reference	
	- [View API Refence](#Customer-API-REST-Reference)	

## Environment information
---
- [Mock environment information - emulated service URL, scenarios mindmap and test data](#mock-environment-information)

- [Test environment information - test scenarios report template ](#test-environment-information)

- [Production environment information - URL endpoint](#production-environment-information)

## Supporting services
---- 

Service: Identity and access - view: [How to integrate, OAuth, JWT requests and responses message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)

<a name="Sample-Messages"></a>
## Sample messages

| Service | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | :--: | -- | -- | -- | 
| customer | `200` | Successfull Request | [Request](sample%20messages/POST_200_customer_request.json) | [Response](sample%20messages/POST_200_customer_response.json) | 
| customer | `400` | Non-existent IRD number | [Request](sample%20messages/POST_400_customer_CST404_non-existent_IRD_number_request.json) | [Response](sample%20messages/POST_400_customer_CST404_non-existent_IRD_number_response.json) |
| customer | `400` | Hyphenated IRD number | [Request](sample%20messages/POST_400_customer_EV1100_hyphenated_IRD_number_request.json) | [Response](sample%20messages/POST_400_customer_EV1100_hyphenated_IRD_number_response.json) |
| customer | `400` | Missing CustomerIDType | [Request](sample%20messages/POST_400_customer_EV1100_missing_CustomerIDType_request.json) | [Response](sample%20messages/POST_400_customer_EV1100_missing_CustomerIDType_response.json) |



<a name="Customer-API-REST-Reference"></a>
## Customer API REST Reference

#### Customer API - `/gateway/customer/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| customer | `POST` | This web service is used to get information about a Customer |
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should validate the service and credential configuration |

> The `status` service is not available in the mock environemnts. 

<a name="mock-environment-information"></a>
## Mock environment information
---
### Mock emulated service URL
| End point|  URL|
|--|--|
 Landing Page | https://mock-cus.ird.digitalpartner.services
 Service Path | https://mock-cus.ird.digitalpartner.services/gateway/customer/|

### Customer mock scenarios mindmap

- [View larger image](../images/Customer%20API%20Mock%20Service.png)
![Mock Scenarios](../images/Customer%20API%20Mock%20Service.png)

> **NOTE:** The emulated service is not managing authentication. Access delegation/restriction is not emulated and any user has access to the test data.

### Test scenarios report template

- [Download Test Scenarios report template](Customer%20API-%20Test%20Report%20Template.docx) - *Coming Soon*


<a name="production-environment-information"></a>
## Production environment information
---
### Production environment URL

* URL Base Path endpoint: https://services.ird.govt.nz:4046/gateway/customer/