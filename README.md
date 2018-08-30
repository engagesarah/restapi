EngageBay REST API
=================
[EngageBay](https://www.engagebay.com/) is a simple, affordable all-in-one marketing and sales software built for small businesses. Get the power of an enterprise software at a fraction of the cost.
### Overview
API is in active development. Currently it allows you to:
- Contacts
- Companies
- Deals
- Tasks
- Forms

### Authentication
This is an HTTPS-only API. Authentications are performed based on respective API Key of the user.

The API key should pass as header with the name "Authentication".

###### API Key
You can find your API Key in the EngageBay Account Admin Settings -> API -> API Key.

###### End Points
All API requests should be made to: https://app.engagebay.com/dev/

Note: All data is case-sensitive. Emails, names and other values are case sensitive. For example, "Test" and "test" are considered two different words.

### Getting Started

**[Contacts](#1-contacts---companies-api)**
* [1 Listing contacts](#11-listing-contacts-)
* [2 Get contact by ID](#12-get-contact-by-id)
* [3 Creating a contact](#13-creating-a-contact-)
* [4 Updating contact](#14-updating-contact-)
* [5 Delete single contact](#15-delete-single-contact-)
* [6 Adding tags to a contact based on email](#16-adding-tags-to-a-contact-based-on-email-)
* [7 Delete tags to a contact based on email](#17-delete-tags-to-a-contact-based-on-email-)
* [8 List tags for a contact](#18-list-tags-for-a-contact-)
* [9 Add score to a contact using email ID](#19-add-score-to-a-contact-using-email-id-)

**[Company APIs](#21-creating-a-company)**

* [1 Creating a company](#21-creating-a-company-)
* [2 Updating a company](#22-updating-a-company-)
* [3 Get list of companies](#23-get-list-of-companies-)
* [4 Get company by id](#24-get-company-by-id-)
* [5 Delete single company](#25-delete-single-company-)

**[Deals](#31-listing-deals)**

* [1 Listing deals](#31-listing-deals-)
* [2 Get deal by its ID](#32-get-deal-by-its-id-)
* [3 Create deal](#33-create-deal)
* [4 Create deal to a contact using email ID](#34-create-deal-to-a-contact-using-email-id)
* [6 Delete deal](#36-delete-deal)
* [7 Get deals from default track grouped by milestones](#37-get-deals-from-default-track-grouped-by-milestones)
* [8 Get deals for a particular track (grouped by milestone)](#38-get-deals-for-a-particular-track-grouped-by-milestone)
* [9 Get deals from particular track](#39-get-deals-from-particular-track)
* [10 Get deals related to specific contact](#310-get-deals-related-to-specific-contact)

### 1.1 Listing contacts : 
- Returns a list of your contacts

For the Response in the Json format, add the header 'Accept' as application/json. By default, the response will be in XML format. Paging can be applied using the page_size and cursor query parameters. Count of the contacts will be in the first contact and Cursor for the next page will be in the last contact of the list. If there is no cursor, it means that it is the end of list.

###### Endpoint
POST dev/api/panel/subscribers

###### Optional parameters
- ``page_size `` - Pagesize for paginated results.
- ``sort_key`` - Sort order for results.

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers?page_size=20&cursor=Cl0KFgoMY3JlYXRlZF90aW1lEgYI2IWV3AUSP2oRYWNjb3VudGJveC0xNTQ2MDVyFwsSClN1YnNjcmliZXIYgICAgIDAowgMogEQNTYyOTQ5OTUzNDIxMzEyMBgAIAE \
-H "Accept : application/json" \
-v -u sample@engagebay.com:123456 
```

###### Example JSON response
```javascript
[
  {
	"id": 4997280348241920,
	"owner_id": 6192449487634432,
	"name": "Test Contact",
	"firstname": "Test Contact",
	"lastname": "1",
	"fullname": "Test Contact 1",
	"name_sort": "test contact",
	"email": "testcontact@gmail.com",
	"created_time": 1535538585,
	"updated_time": 0,
	"status": "CONFIRMED",
	"sources": [{
		"type": "DEFAULT",
		"subscribed_on": 1535538585,
		"status": "ACTIVE",
		"custom": 0
	}],
	"companyIds": [5278755324952576],
	"contactIds": [],
	"properties": [{
		"name": "name",
		"value": "Test Contact",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "last_name",
		"value": "1",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "testcontact@gmail.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "phone",
		"value": "+91 9999999999",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "country",
		"value": "United States",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"listIds": [],
	"owner": {
		"id": 6192449487634432,
		"email": "test@test.com",
		"name": "test"
	},
	"entiy_group_name": "subscriber",
	"tags": [{
		"tag": "United States",
		"assigned_time": 1535538585
	}],
	"broadcastIds": [],
	"openedLinks": [],
	"emailProperties": [],
	"unsubscribeList": [],
	"emailBounceStatus": [],
	"importedEntity": false,
	"forceCreate": false,
	"forceUpdate": false,
	"score": 5
},{
	"cursor": "Cl0KFgoMY3JlYXRlZF90aW1lEgYI2IWV3AUSP2oRYWNjb3VudGJveC0xNTQ2MDVyFwsSClN1YnNjcmliZXIYgICAgIDAowgMogEQNTYyOTQ5OTUzNDIxMzEyMBgAIAE",
	"id": 4659730278514688,
	"owner_id": 6192449487634432,
	"name": "Test contact 2",
	"firstname": "Test contact",
	"lastname": "2",
	"fullname": "Test contact 2",
	"name_sort": "test",
	"email": "test@engagebay.com",
	"created_time": 1535460056,
	"updated_time": 1535529626,
	"status": "UNCONFIRMED",
	"sources": [{
		"type": "DEFAULT",
		"subscribed_on": 1535460056,
		"status": "ACTIVE",
		"custom": 0
	}],
	"companyIds": [],
	"contactIds": [],
	"properties": [{
		"name": "name",
		"value": "test contact",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "last_name",
		"value": "2",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "test@engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "phone",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "country",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"listIds": [],
	"owner": {
		"id": 6192449487634432,
		"email": "test@test.com",
		"name": "test"
	},
	"entiy_group_name": "subscriber",
	"tags": [],
	"broadcastIds": [6084697348112384],
	"openedLinks": [],
	"emailProperties": [{
		"emailDbId": 6119881720201216,
		"entityId": 6084697348112384,
		"sentAt": 1535529626,
		"status": "SENT_6084697348112384"
	}],
	"unsubscribeList": [],
	"emailBounceStatus": [],
	"importedEntity": false,
	"forceCreate": false,
	"forceUpdate": false,
	"score": 5
}]
```
### 1.2 Get contact by ID
Returns data for a single contact
###### Endpoint
GET /dev/api/panel/subscribers/{id}
###### Required parameters
``id`` - Contact Id.
###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/1
-H "Accept : application/json" \
-v -u sample@engagebay.com:123456 
```
###### Example JSON response
```javascript
[{
	"id": 4997280348241920,
	"owner_id": 6192449487634432,
	"name": "Test Contact",
	"firstname": "Test Contact",
	"lastname": "1",
	"fullname": "Test Contact 1",
	"name_sort": "test contact",
	"email": "testcontact@gmail.com",
	"created_time": 1535538585,
	"updated_time": 0,
	"status": "CONFIRMED",
	"sources": [{
		"type": "DEFAULT",
		"subscribed_on": 1535538585,
		"status": "ACTIVE",
		"custom": 0
	}],
	"companyIds": [5278755324952576],
	"contactIds": [],
	"properties": [{
		"name": "name",
		"value": "Test Contact",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "last_name",
		"value": "1",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "testcontact@gmail.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "phone",
		"value": "+91 9999999999",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "country",
		"value": "United States",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"listIds": [],
	"owner": {
		"id": 6192449487634432,
		"email": "test@test.com",
		"name": "test"
	},
	"entiy_group_name": "subscriber",
	"tags": [{
		"tag": "United States",
		"assigned_time": 1535538585
	}],
	"broadcastIds": [],
	"openedLinks": [],
	"emailProperties": [],
	"unsubscribeList": [],
	"emailBounceStatus": [],
	"importedEntity": false,
	"forceCreate": false,
	"forceUpdate": false,
	"score": 5
}]
```
### 1.3 Creating a contact :  

Accepts contact JSON as post data along with the credentials of domain User (User name and API Key).
- Each field is case sensitive.
- Please don't pass null value.
- If you don't know value of field then either don't pass that field or pass empty data to a field.

###### Endpoint
Method POST dev/api/panel/subscribers/subscriber

###### Acceptable request Representation:
```
{
	"score" : 10,
	"properties": [{
		"name": "name",
		"value": "sample",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	},{
		"name": "email",
		"value": "samplecontact@engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "phone",
		"value": "+91 9999999999",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "custom",
		"value": "cutom",
		"field_type": "TEXT",
		"is_searchable": true,
		"type": "CUSTOM"
	}],
	"tags" : [{"tag": "sample"}]
}
```
###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/subscriber \
-H "Accept : application/json" \
-H "Content-Type: application/json" \
-d '{
	"score" : 10,
	"properties": [{
		"name": "name",
		"value": "sample",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	},{
		"name": "email",
		"value": "samplecontact@engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "phone",
		"value": "+91 9999999999",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "custom",
		"value": "cutom",
		"field_type": "TEXT",
		"is_searchable": true,
		"type": "CUSTOM"
	}],
	"tags" : [{"tag": "sample"}]
}' \
-v -u sample@engagebay.com:123456 -X POST
```
### 1.4 Updating contact : 
- Updates the information for a single contact.

We can update required property fields of the contact using this call. It is used to add the new property or update the existing property. It accepts property object of contact with valid parameter in it. We need to send the ContactId of the contact to identify it. This will not affect other fields.

###### Endpoint
PUT dev/api/panel/subscribers/subscriber

###### Optional parameters
- ``first_name``- Updated first name for the contact.
- ``properties`` - Updated custom fields for your contact as object of key/value pairs.

###### Acceptable request representation
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/subscriber \
-H "Accept : application/json" \
-H "Content-Type: application/json" \
-d '{
    "id": 6218728647688192,
    "properties": [{
		"name": "name",
		"value": "test",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "last_name",
		"value": "testlast",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "sarah@engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}]
}' \
-v -u sample@engagebay.com:123456 -X PUT
```
### 1.5 Delete single contact : 
- Delete the single contact from account
###### Endpoint
DELETE dev/api/panel/subscribers/{contact-id}

###### Example Request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/{contact-id}  \
-v -u {email}:{apikey} -X DELETE
```

### 1.6 Adding tags to a contact based on email : 
Searches for the contact based on the given email address and adds the given tags to the contact. You can add multiple tags. Tags should be sent as an array. Email address (email) and tags (tags) array should be sent as a form parameter (Content-Type: application/x-www-form-urlencoded ).Tag name should start with an alphabet and can not contain special characters other than underscore and space.
###### Endpoint
POST dev/api/panel/subscribers/email/tags/add
###### Required parameters
``Email`` - Contact email
``tags`` -  Tags need to add contact

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/email/tags/add -H "Accept: application/json" \
-H "Content-Type :application/x-www-form-urlencoded" \
-d 'email=samson@engagebay.com&tags=["testsample"]' \
-v -u sample@engagebay.com:123456 -X POST
```
### 1.7 Delete tags to a contact based on email : 
Searches for the contact based on the given email address and searches for the given tag in the contact's tag list. If there is a match, then it deletes that tag. You can delete multiple tags. Tags should be sent as an array. Email address (email) and tags (tags) array should be sent as a form parameter(Content-Type: application/x-www-form-urlencoded )
###### Endpoint
POST dev/api/panel/subscribers/email/tags/delete
###### Required parameters
``Email`` - Contact email
``tags`` -  Tags need to add contact

###### Example request
```sh
curl https://app.engagebay.com/dev/api/contacts/email/tags/delete -H "Accept: application/json"
-H "Content-Type :application/x-www-form-urlencoded" \
-d 'email=sample@engagebay.com&tags=["sampletest"]' \
-v -u sarah@engagebay.com:123456 -X POST
```

### 1.8 List tags for a contact : 
Lists all the tags for a contact.
###### Endpoint
POST dev/api/panel/subscribers/get-tags/{subscriber-email}
###### Required parameters
``Email`` - Contact email

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/get-tags/{subscriber-email} -H "Accept: application/json"
-H "Content-Type :application/x-www-form-urlencoded" \
-v -u sarah@engagebay.com:123456 -X POST
```
### 1.9 Add score to a contact using email ID : 
It is used to change the score of the contact using the email address.
###### Endpoint
POST dev/api/panel/subscribers/add-score
###### Required parameters
``Email`` - Contact email
``score`` - Score value

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/subscribers/add-score -H "Accept: application/json" \
-H "Content-Type :application/x-www-form-urlencoded" \
-d 'email=samson@walt.ltd&score=100' \
-v -u sarah@engagebay.com:123456 -X POST
```
### 2.1 Creating a company : 
- Accepts company JSON as post data along with the credentials of domain User (User name and API Key).
- Each field is case sensitive.
- Please don't pass null value.
- If you don't know value of field then either don't pass that field or pass empty data to a field.
###### Endpoint
POST dev/api/panel/companies/company
######  Acceptable request representation:
```javascript
{
	"name": "www.engagebay.com",
	"name_sort": "www.engagebay.com",
	"url": "www.engagebay.com",
	"created_time": 1535620529,
	"updated_time": 0,
	"properties": [{
		"name": "url",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"companyIds": []
}
```
###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/companies/company \
-H "Accept : application/json" \
-H "Content-Type: application/json" \
-d '{
	"name": "www.engagebay.com",
	"name_sort": "www.engagebay.com",
	"url": "www.engagebay.com",
	"created_time": 1535620529,
	"updated_time": 0,
	"properties": [{
		"name": "url",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"companyIds": []
} ' \
-v -u sarah@engagebay.com:123456 -X POST
```
### 2.2 Updating a company : 
We can update required property fields of the company using this call. It is used to add the new property or update the existing property. It accepts property object of company with valid parameter in it. We need to send the Company-Id of the company to identify it. This will not affect other fields.

###### Endpoint
PUT dev/api/panel/companies/company
######  Acceptable request representation:
```javascript
{
	"id": 5141586283331584,
	"name": "www.engagebay.com",
	"name_sort": "www.engagebay.com",
	"url": "www.engagebay.com",
	"created_time": 1535620529,
	"updated_time": 0,
	"properties": [{
		"name": "url",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"companyIds": []
}
```
###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/companies/company \
-H "Accept : application/json" \
-H "Content-Type: application/json" \
-d '{
	"id": 5141586283331584,
	"name": "www.engagebay.com",
	"name_sort": "www.engagebay.com",
	"url": "www.engagebay.com",
	"created_time": 1535620529,
	"updated_time": 0,
	"properties": [{
		"name": "url",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"companyIds": []
} ' \
-v -u sarah@engagebay.com:123456 -X POST
```
### 2.3 Get list of companies : 
- Get list of companies

Fetches list of companies. Page_size,sort_key and cursor should be sent as a form parameter (Content-Type: application/x-www-form-urlencoded ).Paging can be applied using the page_size and cursor form parameters. Cursor for the next page will be in the last company of the list. If there is no cursor, it means that it is the end of list.

###### Endpoint
POST dev/api/panel/companies

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/companies \
-H "Accept: application/json" \
-H "Content-Type :application/x-www-form-urlencoded" \
-d 'page_size=10&sort_key=-created_time&cursor=ClMKFgoMY3JlYXRlZF90aW1lEgYI-rbWrgUSNWoRc35hZ2lsZS1jcm0tY2xvdWRyFAsSB0NvbnRhY3QYgICAkNv0nQoMogEJZ2hhbnNoeWFtGAAgAQ' \
-v -u sarah@engagebay.com:123456 -X POST
```

###### Example JSON response
```
[{
	"id": 5670864666230784,
	"name": "www.github.com",
	"name_sort": "www.github.com",
	"url": "www.github.com",
	"created_time": 1535622004,
	"updated_time": 0,
	"properties": [{
		"name": "url",
		"value": "www.github.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.github.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"owner_id": 5636470266134528,
	"owner": {
		"id": 5636470266134528,
		"email": "sarah@engagehub.io",
		"name": "sarah"
	},
	"importedEntity": false,
	"forceCreate": false,
	"companyIds": []
}, {
	"id": 5141586283331584,
	"name": "www.engagebay.com",
	"name_sort": "www.engagebay.com",
	"url": "www.engagebay.com",
	"created_time": 1535620529,
	"updated_time": 0,
	"properties": [{
		"name": "url",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"owner_id": 5636470266134528,
	"owner": {
		"id": 5636470266134528,
		"email": "sarah@engagehub.io",
		"name": "sarah"
	},
	"importedEntity": false,
	"forceCreate": false,
	"companyIds": []
}]
```
### 2.4 Get company by ID : 
- Returns company object which is associated with given company id

###### Endpoint
GET dev/api/panel/companies/{id}

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/companies/{id} -H "Accept :application/json" 
-v -u {email}:{apikey}
```

###### Example JSON response
```
{
	"id": 5141586283331584,
	"name": "www.engagebay.com",
	"name_sort": "www.engagebay.com",
	"url": "www.engagebay.com",
	"created_time": 1535620529,
	"updated_time": 1535622374,
	"properties": [{
		"name": "url",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "name",
		"value": "www.engagebay.com",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}, {
		"name": "email",
		"value": "",
		"field_type": "TEXT",
		"is_searchable": false,
		"type": "SYSTEM"
	}],
	"tags": [],
	"contactIds": [],
	"entiy_group_name": "company",
	"owner_id": 5636470266134528,
	"owner": {
		"id": 5636470266134528,
		"email": "sarah@engagehub.io",
		"name": "sarah"
	},
	"importedEntity": false,
	"forceCreate": false,
	"companyIds": []
}
```

### 2.5 Delete single company : 
- Deletes company based on the id of the company, which is sent in request url path.

###### Endpoint
DELETE dev/api/panel/companies/{id}

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/companies/{id}  \
-v -u {email}:{apikey} -X DELETE
```

### 3.1 Listing deals : 
Returns list of all "Deals" in the domain in JSON format, which are ordered by created time. Paging can be applied using the page_size and cursor query parameters. Count of the deals will be in the first deal and the cursor for the next page will be in the last deal of the list. If there is no cursor, it means that it is the end of the list.

###### Endpoint
POST dev/api/panel/deals

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/deals?page_size=10&cursor=E-ABAIICNGoRc35hZ2lsZS1jcm0tY2xvdWRyFAsSB0NvbnRhY3QYgICAgKLThAoMogEIcHJhYmF0aGuIAgAU -H  "Accept:application/json" -v -u {email}:{API Key}
```
######  Example JSON response
```
[{
	"id": 6267486190174208,
	"name": "sample deal",
	"amount": 100,
	"closed_date": 1533126840,
	"track_id": 5151135505580032,
	"milestoneLabelName": "New",
	"tags": [],
	"properties": [],
	"probability": 0.1,
	"owner": {
		"id": 5154169597984768,
		"email": "sample@engagebay.com",
		"name": "sample"
	}]
```
### 3.2 Get deal by its ID : 
Gets the deal with the given ID.

###### Endpoint
GET dev/api/panel/deals/{id}

###### Example request
```sh
curl https://app.engagebay.com/dev/api/panel/deals/1234 -H  "Accept : application/json" -v -u {email}:{API Key}
```
######  Example JSON response
```
{
	"id": 1234,
	"name": "sample deal",
	"amount": 100,
	"closed_date": 1533126840,
	"track_id": 5151135505580032,
	"milestoneLabelName": "New",
	"tags": [],
	"properties": [],
	"probability": 0.1,
	"owner": {
		"id": 5154169597984768,
		"email": "harry123@yopmail.com",
		"name": "checkharry"
}
```







