# Authentication Microservice

###overview
This microservice handles authentication that provides access to all andela's microservices.

## Retrieve all users

```http
GET /api/v1/users HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/users"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "email": "john_doe@gmail.com",
    "first_name": "John",
    "last_name": "Doe",
    "name": "John Doe",
    "access_token": "12%67^&(as12",
    "picture": "http://andela/john/myavatarurl",
    "role_id": 1
  },
  {
    "id": 2,
    "email": "jane_doe@andela.com",
    "first_name": "Jane",
    "last_name": "Doe",
    "name": "Jane Doe",
    "access_token": "12asd()^&2",
    "picture": "http://andela/jane/myavatarurl",
    "role_id": 2
  }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/users`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 1 | Helps paginate the collection.
limit | 10 | returns the first ten records of a particular page

## Retrieve a single user

```http
GET /api/v1/users/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/users/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

This endpoint retrieves a single user.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/users`

### Query Parameters

Parameter | Description
--------- | -----------
id | user id

## Create a user

```http
POST /api/v1/users HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

```shell
curl "POST -H 'Authorization: <jwt token>' -d {"email": "john_doe@gmail.com",
  "first_name": "John", "last_name": "Doe", "name": "John Doe",
  "access_token": "12%67^&(as12", "picture": "http://andela/john/myavatarurl", "role_id": 1 }
http://api-gateway.andela.com/api/v1/users"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

This endpoint create a user.

### HTTP Request

`POST http://api-gateway.andela.com/api/v1/users`

### Request Body

Parameter | Description
--------- | -----------------
id | user id
email | user email
first_name | user first name
last_name | user last name
name | user full name
access_token | user jwt token
picture | url of user avatar
role_id | id of user role

## Update a user

```http
PUT /api/v1/users/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "id": 1
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

```shell
curl "PUT -H 'Authorization: <jwt token>' -d {"id": 1, "email": "john_doe@gmail.com",
  "first_name": "John", "last_name": "Doe", "name": "John Doe",
  "access_token": "12%67^&(as12", "picture": "http://andela/john/myavatarurl", "role_id": 1 }
http://api-gateway.andela.com/api/v1/users/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

This endpoint updates a user.

### HTTP Request

`PUT http://api-gateway.andela.com/api/v1/users/<id>`

### Request Body

Parameter | Description
--------- | -----------------
id | user id
email | user email
first_name | user first name
last_name | user last name
name | user full name
access_token | user jwt token
picture | url of user avatar
role_id | id of user role

## Suspend a user

This endpoint suspends a single user.

```http
PUT /api/v1/users/<id>/suspends HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "PUT -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/users/<id>/suspend"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/users/<id>/suspend`

### Query Parameters

Parameter | Description
--------- | -----------
id | user id

## Restore a user

This endpoint restores a single user.

```http
PUT /api/v1/users/<id>/restore HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "PUT -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/users/<id>/restore"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "email": "john_doe@gmail.com",
  "first_name": "John",
  "last_name": "Doe",
  "name": "John Doe",
  "access_token": "12%67^&(as12",
  "picture": "http://andela/john/myavatarurl",
  "role_id": 1
}
```

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/users/<id>/restore`

### Query Parameters

Parameter | Description
--------- | -----------
id | user id

## Create a user role

```http
POST /api/v1/userroles/ HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "name": "admin",
  "permissions": [
  {
    'id': 21,
    'name': 'permission_name',
    'key': 'perm123'
  },
  {
    'id': 12,
    'name': 'permission_name',
    'key': 'perm456'
  }]
}
```

```shell
curl "POST -H 'Authorization: <jwt token>'
-d { "name": "admin", "permissions": [{'id': 21, 'name': 'permission_name', 'key': 'perm123'},
  { 'id': 12, 'name': 'permission_name', 'key': 'perm456'}]}
http://api-gateway.andela.com/api/v1/userroles"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "admin",
  "permissions": [
  {
    "id": 21,
    "name": "permission_name",
    "key": "perm123"
  },
  {
    "id": 12,
    "name": "permission_name",
    "key": "perm456"
  }]
}
```

This endpoint creates a user role.

### HTTP Request

`POST http://api-gateway.andela.com/api/v1/userroles`

### Request Body

Parameter | Description
--------- | -----------------
name | role name
permissions | an array of permissions available to this role

## Update a user role

```http
PUT /api/v1/userroles/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "id": 1,
  "name": "admin",
  "permissions": [
  {
    'id': 21,
    'name': 'permission_name',
    'key': 'perm123'
  },
  {
    'id': 12,
    'name': 'permission_name',
    'key': 'perm456'
  }]
}
```

```shell
curl "PUT -H 'Authorization: <jwt token>'
-d { "id": 1, "name": "admin", "permissions": [{'id': 21, 'name': 'permission_name', 'key': 'perm123'},
  { 'id': 12, 'name': 'permission_name', 'key': 'perm456'}]}
http://api-gateway.andela.com/api/v1/userroles/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 21,
  "name": "admin",
  "permissions": [
  {
    "id": 21,
    "name": "permission_name",
    "key": "perm123"
  },
  {
    "id": 12,
    "name": "permission_name",
    "key": "perm456"
  }]
}
```

This endpoint updates a user role.

### HTTP Request

`POST http://api-gateway.andela.com/api/v1/userroles/<id>`

### Request Parameters

Parameter | Description
---------- | -----------
id | id of the user role

## Find a user role
```http
GET /api/v1/userroles/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/userroles/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "admin",
  "permissions": [
  {
    "id": 21,
    "name": "permission_name",
    "key": "perm123"
  },
  {
    "id": 12,
    "name": "permission_name",
    "key": "perm456"
  }]
}
```

This endpoint finds a user role.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/userroles/<id>`

### Request Parameters

Parameter | Description
--------- | -----------------
id | user role id

## Assign role to users

```http
PUT /api/v1/userroles/assign HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "id": 1,
  "email": ["john_doe@andela.com", "jane_doe@andela.com"]
}
```

```shell
curl "PUT -H 'Authorization: <jwt token>'
-d { "id": 1, "email": ["john_doe@andela.com", "jane_doe@andela.com"] }
http://api-gateway.andela.com/api/v1/userroles/assign"
```

> The above command returns JSON structured like this:

```json
{
  "message": "Users successfully assigned"
}
```

This endpoint assigns an endpoint to a user.

### HTTP Request

`PUT http://api-gateway.andela.com/api/v1/userroles/assign`

### Request Body

Parameter | Description
--------- | -----------------
id | request id
email | an array of user emails

## Unassign role from users

```http
PUT /api/v1/userroles/unassign HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "id": 1,
  "email": ["john_doe@andela.com", "jane_doe@andela.com"]
}
```

```shell
curl "PUT -H 'Authorization: <jwt token>'
-d { "id": 1, "email": ["john_doe@andela.com", "jane_doe@andela.com"] }
http://api-gateway.andela.com/api/v1/userroles/unassign"
```

> The above command returns JSON structured like this:

```json
{
  "message": "Users unassigned successfully"
}
```

This endpoint unassigns an array of users from a role.

### HTTP Request

`PUT http://api-gateway.andela.com/api/v1/userroles/unassign`

### Request Body

Parameter | Description
--------- | -----------------
id | request id
email | an array of user emails

## Get all permissions

This endpoint returns all permissions

```http
GET /api/v1/permissions HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/permissions"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "permission_one",
    "key": "123abc"
  },
  {
    "id": 2,
    "name": "permission_two",
    "key": "456def"
  },
  {
    "id": 3,
    "name": "permission_three",
    "key": "789ghi"
  },
]
```

### HTTP Request

`PUT http://api-gateway.andela.com/api/v1/permissions`
