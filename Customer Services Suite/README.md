
![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Customer Services Suite
#### Release version 1.0 

## About the Customer Services Suite
The 'Customer Services Suite’ is collection of APIs designed to be used together — Account, Address, Bank, Contact, Customer, Name and Period. It is 
important to understand the dependencies between these when deciding which ones to implement, how to correctly sequence their adoption, how authorisation rules 
impact access, and how to use them in general. 

![Customer APIs](images/customer%20DM3.png)
Larger View [Customer APIs](images/customer%20DM3.png)


### [Account API](Account%20API) _(Read-only)_
Account API provides general information about an identified customer’s accounts.

### [Address API](Address%20API)
Address API updates customer and account addresses.

### [Bank API](Bank%20API) 
Bank Account API updates refund bank account information of an identified customer’s account.

### [BIC API](BIC%20API) 
BIC API updates of the BIC codes information of an identified for a customer’s account.

### [Contact API](Contact%20API) 
Contact API updates customer and account contacts.

### [Customer API](Customer%20API) _(Read-only)_
Customer API provides general information about a customer. 

### [Name API](Name%20API)
Name API updates customer names.

### [Period API](Period%20API) _(Read-only)_
Period API provides information about periods for an identified customer’s account. 

---


## Customer Services Suite REST API reference

You'll need to use different APIs depending on the service that your app provides. Use the following tables to see which APIs are useful for different kinds of operations.

#### Account API - `/gateway/account/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| account | `POST` | Returns the information of an identified customer account | 
| list | `POST` | Returns a list of accounts for an identified customer | 

---

#### Address API - `/gateway/address/{Service}`
| Service | HTTP request types | Description |
| -- | :--: | -- | 
| address | `DELETE` | Deletes the details of the identified address - this can be either a customer address or an account address | 
| address | `PUT` | Updates the provided details to the identified address - this can be either a customer address or an account address | 
| address | `POST` | Adds an address of a given type (physical/postal) to the identified customer<br/>or<br/>Adds an address of a given type (physical/postal) to the identified account | 

---

#### Bank API - `/gateway/bank/{Service}`
| Service | HTTP request types | Description | 
| -- | :--: | -- | 
| bank |  `DELETE` | Deletes the refund bank account from the identified customer account |
| bank |  `POST` | Adds a refund bank account to the identified customer account if there is not already a refund bank account on the customer account<br/>Or<br/>Replaces an existing refund bank account on the identified customer account  |

---

#### BIC API - `/gateway/bank/{Service}`
| Service | HTTP request types | Description | 
| -- | :--: | -- | 
| bic |  `DELETE` | Adds new or updates existing BIC code to customer |
| bic |  `POST` | Ceases an existing BIC code on a customer  |

---

#### Contact API - `/gateway/contact/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| contact | `POST` | Adds a contact to the identified customer<br/>or<br/>Adds a contact to the identified account | 
| contact | `PUT` | Updates the name of an identified contact - this can be either a customer contact or an account contact | 
| contact | `DELETE` | This web service is used to delete a contact | 
| phone | `POST` | Adds a phone number to the contact details of an identified customer<br/>or<br/>Adds a phone number to the contact details of an identified account | 
| phone | `PUT` | Updates the phone number of an identified contact - this can be either a customer contact phone number or an account contact phone number | 
| phone | `DELETE` | Deletes the phone number of an identified contact - this can be either a customer contact phone number or an account contact phone number | 

---

#### Customer API - `/gateway/customer/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| customer | `POST` | Returns the information of an identified customer |

---

#### Name API - `/gateway/name/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| name | `POST` | Adds a name of a given type (preferred/trading) to the customer data set |
| name | `PUT` | Updates the details of an existing name in the customer data set |
| name | `DELETE` | Deletes a given name from the customer data set |

---

#### Period API - `/gateway/period/{Service}`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| list | `POST` | Returns the information of periods for an identified customer account | 

---

#### Common across all APis - `/gateway/{api}/status`
| Service | HTTP request types | Description | 
| :--: | :--: | -- |
| status | `GET` | This web service sends a 200 HTTP response with a message body of "OK". This is preferred over service "ping" functionality as this should *only* be used to validate the service and credential configuration | 