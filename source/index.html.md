---
noteId: "df220f70ac4e11ebae90cb6b7a3e51d7"
tags: []
title: "API Reference"
language_tabs:
  - "javascript"
  - "ruby"
toc_footers:
  - "<a href='#'>Sign Up for a Developer Key</a>"
  - "<a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>"
includes:
  - "errors"
search: true
code_clipboard: true
---

# Introduction

Welcome to the FIND YOUR HOUSE API! You can use our API to access FIND YOUR HOUSE API endpoints, which can get information on various houses in our database.

The FIND YOUR HOUSE API is organized around REST. Our API has predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

We have language bindings in Ruby, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

Our API is able to support user accounts with each user having the ability managing their own resources.
In order to get your API key, you need to Signup or login!

## Signup

> Signup a new user - get token from here

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/signup")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request.body = "{
    \"name\": \"guy\",
    \"email\": \"guy@email.com\",
    \"password\": \"1234\",
    \"password_confirmation\": \"1234\"
}"

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://find-your-house-backend.herokuapp.com/signup",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    name: "guy",
    email: "guy@email.com",
    password: "1234",
    password_confirmation: "1234",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "message": "Account created successfully",
  "auth_token": "*************"
}
```

> Make sure that your API key is located in `auth_token`. In our our case id `*************`

FIND YOUR HOUSE API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint creates a new user.

### HTTP Request

`POST https://find-your-house-backend.herokuapp.com/signup`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| name                  | string | Name of the user                                    |
| email                 | string | An adress mail. It's must be unique in our database |
| password              | string | A password                                          |
| password_confirmation | string | A confirmation password.                            |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>

<aside class="warning"> If you faild to signup, you'll get this validation message: <code>&lt;"Validation failed: Name can't be blank"&gt;</code></aside>

## login

> login an existing user - get token from here

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/auth/login")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request.body = "{
    \"email\": \"guy@email.com\",
    \"password\": \"1234\"
}"

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://find-your-house-backend.herokuapp.com/auth/login",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    email: "guy@email.com",
    password: "1234",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "auth_token": "*************"
}
```

> Make sure that your API key is located in `auth_token`. In our our case id `*************`

FIND YOUR HOUSE API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint log in an existing user

### HTTP Request

`POST https://find-your-house-backend.herokuapp.com/auth/login`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| email     | string | An adress mail. It's must be unique in our database |
| password  | string | A password                                          |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>

<aside class="warning"> If you faild to signup, you'll get this validation message: <code>&lt;"Invalid credentials"&gt;</code></aside>

## logout

> logout a connected user - use your token

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/users/sign_out")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Delete.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "DELETE",
  url: "https://find-your-house-backend.herokuapp.com/users/sign_out",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "status": "success",
  "message": "Signed out successfully"
}
```

> Make sure to replace `****************` with your API key.

FIND YOUR HOUSE API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint logout an user

### HTTP Request

`DELETE https://find-your-house-backend.herokuapp.com/users/sign_out`

> If you faild to logout, you'll get this message:

```json
{
  "status": "error",
  "error": "Access token is missing in the request"
}
```

# Houses

## Get all houses

> This endpoint retrieves all houses.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/houses")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/houses",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3,
    "price": 200.0,
    "details": "Details 1",
    "about": "Kin house",
    "picture": "www.gbsismwa.me",
    "owner": "1",
    "created_at": "2021-05-03T09:14:30.922Z",
    "updated_at": "2021-05-03T09:14:30.922Z"
  },
  {
    "id": 5,
    "price": 800.0,
    "details": "Details 3",
    "about": "G house",
    "picture": "www.gbsismwa.me",
    "owner": "3",
    "created_at": "2021-05-03T18:11:58.211Z",
    "updated_at": "2021-05-03T18:11:58.211Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves all houses.

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/houses`

## Get a specific house

> This endpoint retrieves a specific houses.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/houses/2")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/houses/2",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 2,
    "price": 200.0,
    "details": "Details House",
    "about": "Kin house",
    "picture": "www.gbsismwa.me",
    "owner": "1",
    "created_at": "2021-05-03T09:14:30.922Z",
    "updated_at": "2021-05-03T09:14:30.922Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves all houses.

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/houses/<ID>`

### Url Parameters

| Parameter | Type    | Description                     |
| --------- | ------- | ------------------------------- |
| ID        | integer | The ID of the house to retrieve |

# Favorites

## Get all user favorites

> This endpoint retrieves all user favorites.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/users/3/favourites")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/users/3/favourites",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3,
    "price": 200.0,
    "details": "Details 1",
    "about": "Kin house",
    "picture": "www.gbsismwa.me",
    "owner": "1",
    "created_at": "2021-05-03T09:14:30.922Z",
    "updated_at": "2021-05-03T09:14:30.922Z"
  },
  {
    "id": 5,
    "price": 800.0,
    "details": "Details 3",
    "about": "G house",
    "picture": "www.gbsismwa.me",
    "owner": "3",
    "created_at": "2021-05-03T18:11:58.211Z",
    "updated_at": "2021-05-03T18:11:58.211Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves all user favorites

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/users/<USERID>/favourites`

### Url Parameters

| Parameter | Type    | Description        |
| --------- | ------- | ------------------ |
| USERID    | integer | The ID of the user |

## Get a specific user favorite

> This endpoint retrieves a specific user favorite.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/users/3/favourites")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/users/3/favourites",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3,
    "price": 200.0,
    "details": "Details House",
    "about": "Kin house",
    "picture": "www.gbsismwa.me",
    "owner": "1",
    "created_at": "2021-05-03T09:14:30.922Z",
    "updated_at": "2021-05-03T09:14:30.922Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves a specific user favorite.

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/users/<USERID>/favourites/<ID>`

### Url Parameter

| Parameter | Type    | Description                                          |
| --------- | ------- | ---------------------------------------------------- |
| ID        | integer | The ID of a specific user favorite house to retrieve |
| USERID    | integer | The ID of the user                                   |
