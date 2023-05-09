![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# IRD Number Validation Service
---
#### Release version 1.0

## About the service
The IRD number validation service is a API that enables the consumer to assess whether the IRD number and the accompanying biographic attributes of a customer are consistent, and therefore whether the IRD number is likely to be correct.

It is important to note that this API service does not return an IRD number.

Additionally, this service does not validate that the information provided in the request is correct, simply that Inland Revenue can identify a customer with enough certainty.  This is especially pertinent to the NZBN, as Inland Revenue does not have a record of every NZBN, and as such the Companies Office should be consulted to verify an NZBN.

>**NOTE:** The IRD Number Validation Service is only available to approved Digital Service Providers who use a X.509 Digital Certificate for Mutual TLS on port 4046 (through a cloud application)  

This service supports the following message type: 
 
* **READ:** Retrieves match from Inland Revenue. Requires an IRD number and other information about the customer. 

--------
## Key documentation

- YAML file:
	- View and download the [v1 Open API definition (YAML)](Customer%20Service%2020220510.yaml)

- IRD number validation build pack
	- [Download the build pack](Build%20pack%20-%20IRD%20Number%20Validation%20Service.pdf) to view data definitions of each operation and response status code definitions
	
* Message samples
	* [View message samples for requests and positive responses](#Message-samples)

## Environment information
- [Mock environment information - Emulated services, mind map and test data, Test scenarios report template and URL endpoints](#mock-environment-information)

- [Production environment information - URL endpoint](#prod-environment-information)

----
## Message samples

- Simulating IRD number validation operations:
    - Request and Response Samples
        -  Sample requests
            - [Request with FormattedName, FormattedAddress and NZBN](sample%20messages/formatted_name_formatted_Address_NZBN.json)
            - [Request with Name and Address](sample%20messages/name_and_address.json)
        -   Positive responses (http 200)
            - [Match](sample%20messages/match-response.json)
            - [No match](sample%20messages/no_match_response.json)
        -   Negative response (http 400)
            - [Error IR002 - The NZBN supplied does not match the customer](sample%20messages/nzbn_does_not_match.json)

----
## Mock environment information

### Mock emulated service URL
| End point|  URL|
|--|--|
| Landing Page | https://irdvalidation.test.services.ird.govt.nz/ |
| ValidateIRD | https://irdvalidation.test.services.ird.govt.nz/gateway/customer-service/validateIRD |

### Mock scenarios mind map

- [View larger image](images/IRD%20Number%20Validation%20API.png)
![Mock Scenarios](images/IRD%20Number%20Validation%20API.png)

### Test data
   - The following test data can be tested in our Mock Services environment when submitting requests to the service operations
   - This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses.

      Scenario ID | Data | Response 
    	--- | --- | ---
    	MOCK-01 | Customer IRD (*identifier*): 123344677 | HTTP Response Code - 200
    	MOCK-02 | Customer IRD (*identifier*): 123344952 | HTTP Response Code - 200
    	MOCK-20 | Customer IRD (*identifier*): 123345002 | HTTP Response Code - 400
    	MOCK-30 | Customer IRD (*identifier*): 123456789 | HTTP Response Code - 400
    	
### Test scenarios report template

- [Download Test Scenarios report template](IRD%20Validation%20Service%20-%20Test%20Report%20Template.docx)

----
## Prod environment information

### Prod environment URL
| End point|  URL|
|--|--|
- Production : https://services.ird.govt.nz:4046/gateway/customer-service/validateIRD
