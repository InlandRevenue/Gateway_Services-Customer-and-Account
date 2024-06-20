
![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Contact API 

#### Release version 1.0  

## About the Contact API 

The contact API enables the creating, updating, and deleting of the contact details of a customer or an account. It is one of eight APIs that together make up the customer services suite. 

>**NOTE:** The Contact API is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 or JWT token.

## Key documentation
* View and download the [Contact API YAML](Contact%202021-09-14.yaml)
* [Download the Contact API build pack](Build%20pack%20-%20Contact%20API.pdf) to view data definitions of each operation and response status code definitions
* [Sample Messages](#Sample-Messages) to a list of successful and errored JSON request messages 
* [Contact API Reference and URL endpoints](#Contact-API-REST-Reference)	

## Environment information
- [Mock environment information - emulated service URL, scenarios mindmap](#mock-environment-information)

## Supporting services
* Service: Identity and access - view: [How to integrate, M2M JWT & OAuth message samples and build pack](https://github.com/InlandRevenue/Gateway_Services-Access/tree/master/Identity%20and%20Access)
* [Customer API](../Customer%20API)
* [Account API](../Account%20API)

---

<a name="Sample-Messages"></a>
### Sample messages

| Service | HTTP request types | HTTP Status Code| Description | JSON Request | JSON Response | 
| -- | -- | :--: | -- | -- | -- | 
| contact | DELETE | 200 | Successful delete contact request | [Request](sample%20messages/DELETE_200_contact_request.json) | Review HTTP status Code  | 
| contact | DELETE | 400 | CST404 - Contact has already been deleted | [Request](sample%20messages/DELETE_400_CST404_contact_already_been_deleted_request.json)| [Response](sample%20messages/DELETE_400_CST404_contact_already_been_deleted_response.json)  |
| contact | POST | 200 | Create account level request | [Request](sample%20messages/POST_200_contact_create_account_level_request.json) | [Response](sample%20messages/POST_200_contact_create_account_level_response.json) | 
| contact | POST | 200 | TAX Agent Linked CST Customer | [Request](sample%20messages/POST_200_contact_TAX_Agent_Linked_CST_Customer_request) | [Response](sample%20messages/POST_200_contact_TAX_Agent_Linked_CST_Customer_response.json) |
| contact | POST | 400 | EV1100 - Contact CustomerIDType not equal to CST or IRD | [Request](sample%20messages/POST_400_EV1100_contact_CustomerIDType_not_equal_to_CST_or_IRD_request.json) | [Response](sample%20messages/POST_400_EV1100_contact_CustomerIDType_not_equal_to_CST_or_IRD_response.json)|
| contact | PUT | 200 | Successful update contact request | [Request](sample%20messages/PUT_200_contact_request)| Review HTTP status Code | 
| phone   | DELETE | 200 | Successful delete phone request | [Request](sample%20messages/DELETE_200_phone_request.json) | Review HTTP status Code  | 
| phone   | POST | 200 | Successful create phone request | [Request](sample%20messages/POST_200_phone_create_request.json) | [Response](sample%20messages/POST_200_phone_create_response.json)  | 
| phone   | PUT | 200 | Successful update phone request | [Request](sample%20messages/PUT_200_phone_request.json) | Review HTTP status Code | 

<a name="Contact-API-REST-Reference"></a>
## Contact API REST Reference

| Environment | Scheme Authority | Mutual TLS (mTLS) authentication |
| --- | --- | :---: |
| Mock (DPS)| `https://customerservices.test.services.ird.govt.nz`| no |
| Production (PROD) | `https://services.ird.govt.nz:4046`| yes |

#### Contact API - `{Scheme Authority}/gateway/contact/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- | 
| contact | `POST` | Adds a contact to the identified customer<br/>or<br/>Adds a contact to the identified account | 
| contact | `PUT` | Updates the name of an identified contact - this can be either a customer contact or an account contact | 
| contact | `DELETE` | This web service is used to delete a contact | 
| phone | `POST` | Adds a phone number to the contact details of an identified customer<br/>or<br/>Adds a phone number to the contact details of an identified account | 
| phone | `PUT` | Updates the phone number of an identified contact - this can be either a customer contact phone number or an account contact phone number | 
| phone | `DELETE` | Deletes the phone number of an identified contact - this can be either a customer contact phone number or an account contact phone number | 
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 

> The `status` service might not be available in the mock environment.



<a name="mock-environment-information"></a>
## Mock environment information
---

### Mock emulated service URL
* Landing Page https://customerservices.test.services.ird.govt.nz


### Contact mock scenarios mindmap

[View larger image](../images/Contact%20API%20Emulator%20Mindmap.png)
![Mock Scenarios](../images/Contact%20API%20Emulator%20Mindmap.png) - *Coming Soon*

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

* [Download Test Scenarios report template](Contact%20API%20-%20Test%20Report%20Template_v1.3.docx)