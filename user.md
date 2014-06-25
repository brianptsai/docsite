# User Service

## GET /v1/user/me

### Description

Request the user object corresponding to the currently logged in user (as specified by the access_token)

### Parameters

Parameter Name | Description
--- | ---
*N/A* | *N/A*

### Example Request

```js
curl -X POST 'https://api.example.com/v1/user/me' --header 'Authorization: Bearer c952fdb2d22412da958df56e0fff782=='
```

### Response

JSON representation of the requested user object.

```js
{
  "data": {
    "id": "17870767387892741278",
    "username": "carey71471",
    "account_status": 0,
    "email": "marty@barrows.biz",
    "first_name": "Tyreek",
    "last_name": "Hammes",
    "date_of_birth": "1974-09-11",
    "registration_ip": "78.241.88.242",
    "locale": "en_US",
    "created_at": "2012-12-31T23:59:59Z",
    "updated_at": "2012-12-31T23:59:59Z",
    "terms_accepted_at": null,
    "receive_news": false,
    "reset_password_sent_at": null,
    "sign_in_count": 0,
    "current_sign_in_at": null,
    "last_sign_in_at": null,
    "current_sign_in_ip": null,
    "last_sign_in_ip": null,
    "anonymous": false,
    "tags": [],
    "external_accounts": [],
    "title_id" : "72737378383838",
    "entity_type": "user"
  },
  "meta": {}
}
```

### Errors

See global errors.

### Notes


## GET /v1/user/users/:id

### Description

Request the user object corresponding to the specified id.

### Parameters

Parameter Name | Description
--- | ---
**id** *required* | *Integer* | The ID of the user to retrieve.

### Example Request

```js
curl -X GET 'https://api.example.com/v1/user/users/17267098420663971439'
```


### Response

JSON representation of the requested user object.

```js
{
  "data": {
    "id": "17870767387892741278",
    "username": "carey71471",
    "account_status": 0,
    "email": "marty@barrows.biz",
    "first_name": "Tyreek",
    "last_name": "Hammes",
    "date_of_birth": "1974-09-11",
    "registration_ip": "78.241.88.242",
    "locale": "en_US",
    "created_at": "2012-12-31T23:59:59Z",
    "updated_at": "2012-12-31T23:59:59Z",
    "terms_accepted_at": null,
    "receive_news": false,
    "reset_password_sent_at": null,
    "sign_in_count": 0,
    "current_sign_in_at": null,
    "last_sign_in_at": null,
    "current_sign_in_ip": null,
    "last_sign_in_ip": null,
    "anonymous": false,
    "tags": [],
    "external_accounts": [],
    "title_id" : "72737378383838",
    "entity_type": "user"
  },
  "meta": {}
}
```

### Errors

* see global errors

### Notes

* none

## POST /v1/user/users (Anonymous)

### Description

Create a new anonymous user record under the title of the current Application. You must specify `anonymous: true` in your request. Additional data is optional and should be provided, if known.

### Parameters
Parameter Name | Example | Description
--- | --- | ---
**data[anonymous]** | `true` | (Boolean) Whether or not this user is anonymous.
**data[registration_ip]** | `127.0.0.1` | (String) The remote IP address of the user submitting the registration request.



### Example Request

```js
curl -X POST 'https://api.example.com/v1/user/users' -d '{
  "data": {
    "anonymous": true,
    "registration_ip": "127.0.0.1"
  }
}'
```
### Response

```js
{
  "data": {
    "id": "2229977376599201407",
    "username": null,
    "account_status": 0,
    "email": null,
    "first_name": null,
    "last_name": null,
    "date_of_birth": null,
    "registration_ip": "127.0.0.1",
    "locale": "en_US",
    "created_at": "2012-12-31T23:59:59Z",
    "updated_at": "2012-12-31T23:59:59Z",
    "terms_accepted_at": null,
    "receive_news": false,
    "reset_password_sent_at": null,
    "sign_in_count": 1,
    "current_sign_in_at": "2012-12-31T23:59:59Z",
    "last_sign_in_at": null,
    "current_sign_in_ip": "127.0.0.1",
    "last_sign_in_ip": null,
    "anonymous": true,
    "tags": [],
    "external_accounts": [],
    "title_id" : "72737378383838",
    "entity_type": "user",
    "password": "Xu3xNtmwMHxLrL0HBXYmXiIm1-E"
  },
  "meta": {

  }
}
```

### Errors

See global errors

### Notes
Anonymous user creation will return a random password used for authentication in the event that both the access_token and refresh_token have expired. !!!This is the only time this password will be returned!!!

## POST /v1/user/users

### Description

Create a new user record under the title of the current Application.

### Parameters

Parameter Name | Example | Description
--- | --- | ---
**data[date_of_birth]** | `1988-09-11` | (Date) Date of birth for the user in `yyyy-mm-dd` format.
**data[registration_ip]** | `125.160.177.30` | (String) The remote IP address of the user submitting the registration request.
**data[email]** | `doug_shields@pollichpredovic.net` | (String) The email address of the user.
**data[first_name]** | `Muriel` | (String) The first name of the user.
**data[last_name]** | `Streich` | (String) The last name of the user.
**data[username]** | `marjolaine50258` | (String) The username of the user.
**data[locale]** | `en_US` | (String) The locale of the user.
**data[password]** | `sup3rs3cr3t` | (String) Plaintext password for the user.
**data[password_confirmation]** | `sup3rs3cr3t` | (String) Confirmation of the plaintext password.
**data[tags]** | `["tag1","tag2"]` | (Array) An array of tags to add to this user.

### Example Request

```js
curl -X POST 'https://api.example.com/v1/user/users' -d '{
  "data": {
    "date_of_birth": "1988-09-11",
    "registration_ip": "125.160.177.30",
    "email": "doug_shields@pollichpredovic.net",
    "first_name": "Muriel",
    "last_name": "Streich",
    "username": "marjolaine50258",
    "locale": "en_US",
    "password": "sup3rs3cr3t",
    "password_confirmation": "sup3rs3cr3t",
    "tags": []
  }
}'
```

### Response

```js
{
  "data": {
    "id": "9452228899694236507",
    "username": "marjolaine50258",
    "account_status": 0,
    "email": "doug_shields@pollichpredovic.net",
    "first_name": "Muriel",
    "last_name": "Streich",
    "date_of_birth": "1988-09-11",
    "registration_ip": "125.160.177.30",
    "locale": "en_US",
    "created_at": "2012-12-31T23:59:59Z",
    "updated_at": "2012-12-31T23:59:59Z",
    "terms_accepted_at": null,
    "receive_news": false,
    "reset_password_sent_at": null,
    "sign_in_count": 1,
    "current_sign_in_at": "2012-12-31T23:59:59Z",
    "last_sign_in_at": null,
    "current_sign_in_ip": "125.160.177.30",
    "last_sign_in_ip": null,
    "anonymous": false,
    "tags": [],
    "external_accounts": [],
    "title_id" : "72737378383838",
    "entity_type": "user"
  },
  "meta": {

  }
}
```

### Errors

See global errors

### Notes


## PUT /v1/user/users/:id


### Description

Update an existing user record.

### Parameters

Parameter Name | Example | Description
--- | --- | ---
**data[date_of_birth]** | `1988-09-11` | (Date) Date of birth for the user in `yyyy-mm-dd` format.
**data[email]** | `doug_shields@pollichpredovic.net` | (String) The email address of the user.
**data[first_name]** | `Muriel` | (String) The first name of the user.
**data[last_name]** | `Streich` | (String) The last name of the user.
**data[locale]** | `en_US` | (String) The locale of the user.
**data[tags]** | `["tag1","tag2"]` | (Array) An array of tags to add to this user

### Example Request

```js
curl -X PUT 'https://api.example.com/v1/user/users/3411286538841124047' -d '{
  "data": {
    "first_name": "Jamaica"
  }
}'
```
### Response

```js
{
  "data": {
    "id": "3411286538841124047",
    "username": "micaela21263",
    "account_status": 0,
    "email": "madie@keelingmcglynn.name",
    "first_name": "Jamaica",
    "last_name": "Reinger",
    "date_of_birth": "1978-09-11",
    "registration_ip": "146.143.12.174",
    "locale": "en_US",
    "created_at": "2012-12-31T23:59:59Z",
    "updated_at": "2013-08-02T12:13:02Z",
    "terms_accepted_at": null,
    "receive_news": false,
    "reset_password_sent_at": null,
    "sign_in_count": 0,
    "current_sign_in_at": null,
    "last_sign_in_at": null,
    "current_sign_in_ip": null,
    "last_sign_in_ip": null,
    "anonymous": false,
    "tags": [],
    "external_accounts": [],
    "title_id" : "72737378383838",
    "entity_type": "user"
  },
  "meta": {}
}
```
### Errors

see global errors

### Notes

Please note that you can not update the title_id of an existing user record.

## External Accounts


### POST /v1/user/users/:id/external_accounts/:provider


#### Description

Link an external account to the specified user.


#### Parameters
Parameter Name | Example | Description
--- | --- | ---
**id**| `17267098420663971439` | (String) The id of the User entity.
**provider**| `facebook` | (String) A string identifying the external account provider.
**external_access_token** | `CAACEdEose0cBAOL9NDZApbl...` | (String) Oauth Access Token from external provider

#### Example Request

```js
curl -X POST 'https://api.example.com/v1/users/10181216645161457797/external_accounts/facebook'
{
  "data": {
    "external_access_token": "CAACEdEose0cBAOL9NDZApbltf3R9gzsoK2ziXNZAb4RdK1RTEq13vVLSTGnMX8587C4YdfjAajzeb4yTVGvnQDVXvLNBT5I5T5HbWGYhPnLOYlAjexDrmhGdczIPKOyxqKxTPoWpTHIH3krxJ7byGNtgAYzQHt0Pm23ZAZBtKcFVWkE3DMsABfZB6JdNzVM3AeyncCApzmgZDZD"
  }
}'
```

#### Response

```js
{
  "data": {
    "id": "12726547651499853016",
    "user_id": "10181216645161457797",
    "provider": "facebook",
    "provider_uid": "123",
    "created_at": "2012-12-31T23:59:59.545Z",
    "updated_at": "2012-12-31T23:59:59.132Z",
    "entity_type": "external_account"
  },
  "meta": {}
}
```

#### Errors

HTTP Code | Internal Code | Name | Description/Metadata
--- | --- | --- | ---
401 | TBA | Unauthorized | You do not have access to modify this user's external accounts. |
400 | TBA | Invalid parameters | Information submitted for the external account was omitted or is invalid. |

#### Notes


### DELETE /v1/user/users/:id/external_accounts/:provider


#### Description

Remove an external account from a user.


#### Parameters
Parameter Name | Example | Description
--- | --- | ---
**id**| `17267098420663971439` | (String) A string identifying the external account provider.
**provider**| `facebook` | (String) A string identifying the external account provider.

### Example Request

```js
curl -X DELETE 'https://api.example.com/v1/users/10181216645161457797/external_accounts/facebook'
```

### Response

```js
{
  "data": {
    "id": "12726547651499853016",
    "user_id": "10181216645161457797",
    "provider": "facebook",
    "provider_uid": "123",
    "created_at": "2012-12-31T23:59:59Z",
    "updated_at": "2012-12-31T23:59:59Z",
    "entity_type": "external_account"
  },
  "meta": {}
}
```

#### Errors

HTTP Code | Internal Code | Name | Description/Metadata
--- | --- | --- | ---
401 | TBA | Unauthorized | You do not have access to modify this user's external accounts. |


#### Notes


### POST /v1/user/users/find_by_external_id


#### Description

Find users by their linked external accounts.


#### Parameters
Parameter Name | Example | Description
--- | --- | ---
**provider**| `facebook` | (String) A string identifying the external account provider.
**provider_uids**| `[ "17267098420663971439", "72670984206639714391" ]` | (Array) An array of external account ids for the given provider.

### Example Request

```js
curl -X POST 'https://api.example.com/v1/user/users/find_by_external_id' -d '{
  "data": {
    "provider": "facebook",
    "provider_uids": [ "17267098420663971439", "72670984206639714391" ]
  }
}'
```

### Response

```js
{
  "data": [
    {
      "id": "7283084392112234632",
      "username": "ryann19755",
      "external_accounts": [
        {
          "id": "3964916442535380394",
          "user_id": "7283084392112234632",
          "provider": "facebook",
          "provider_uid": "17267098420663971439",
          "created_at": "2013-12-10T00:07:25Z",
          "updated_at": "2013-12-10T00:07:25Z",
          "entity_type": "external_account"
        }
      ],
      "entity_type": "user"
    },
    {
      "id": "283084392112234632",
      "username": "seans5984",
      "external_accounts": [
        {
          "id": "9649164425353803943",
          "user_id": "283084392112234632",
          "provider": "facebook",
          "provider_uid": "72670984206639714391",
          "created_at": "2013-12-10T00:07:25Z",
          "updated_at": "2013-12-10T00:07:25Z",
          "entity_type": "external_account"
        }
      ],
      "entity_type": "user"
    }
  ],
  "meta": {}
}
```

#### Errors

HTTP Code | Internal Code | Name | Description/Metadata
--- | --- | --- | ---


#### Notes
