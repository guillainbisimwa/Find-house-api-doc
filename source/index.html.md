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

# Kittens

## Get All Kittens

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

| Parameter    | Default | Description                                                                      |
| ------------ | ------- | -------------------------------------------------------------------------------- |
| include_cats | false   | If set to true, the result will also include cats.                               |
| available    | true    | If set to false, the result will include kittens that have already been adopted. |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |

## Delete a Specific Kitten

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the kitten to delete |
