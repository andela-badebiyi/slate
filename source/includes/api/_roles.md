# Roles Microservice
### Overview
This microservice handles the creating, deleting, updating and fetching of Roles with respect to Andela Fellows


## Get All Roles

```http
GET /api/v1/roles HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>' http://api-gateway.andela.com/api/v1/roles"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Apprentice",
    "level": "D1",
    "skills": [
      {
        "name": "Managing expectation",
        "description": "should be great at managing expectations"
      },
      {
        "name": "stakeholder management",
        "description": "should be proficient in stake holder management"
      }
    ]
  },
  {
    "id": 2,
    "name": "Team Lead",
    "level": "D4",
    "skills": [
      {
        "name": "Managing expectation",
        "description": "should be great at managing expectations"
      },
      {
        "name": "stakeholder management",
        "description": "should be proficient in stake holder management"
      }
    ]
  }
]
```

This endpoint retrieves all roles.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/roles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 1 | Helps paginate the collection.
limit | 10 | returns the first ten records of a particular page

<aside class="success">
Remember — this request has to be authenticated
</aside>

## Get a Specific Role

```http
GET /api/v1/roles/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
 http://api-gateway.andela.com/api/v1/roles/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Team Lead",
  "level": "D4",
  "skills": [
    {
      "name": "Managing expectation",
      "description": "should be great at managing expectations"
    },
    {
      "name": "stakeholder management",
      "description": "should be proficient in stake holder management"
    }
  ]
}
```

This endpoint retrieves a single role.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/roles/<id>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The id of the role to be retrieved

## Create A role

```http
POST /api/v1/roles HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "name": "technical trainer",
  "level": "D4",
  "skills": [3, 4]
}
```

```shell
curl 'POST -H "Authorization: <jwt token>"
-d {"name": "technical trainer", "level": "D4", "skills": [3, 4]}
http://api-gateway.andela.com/api/v1/roles/'
```

> The above command returns JSON structured like this:

```json
{
  "id": "1",
  "name": "technical trainer",
  "level": "d4",
  "skills": [
    {
      "name": "Speaking to be understood",
      "description": "fellow must be able to speak clearly and audibly"
    },
    {
      "name": "expectation management",
      "description": "fellow must be able to adequately manage expectations"
    }
  ]
}
```

This end point creates a new role

### HTTP Request
`POST http://api-gateway.andela.com/api/v1/roles`

### Request Body

title| Description
--------- | -----------
name | name of the role
level | level of fellow that can be assigned to that role
skills | Array containing the skill id's of the skills a fellow at that role should possess

## Update a role

This end point updates an existing role

```http
PATCH /api/v1/roles/<id> HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "name": "Team Lead",
  "level": "D2",
  "skills": [1, 3]
}
```

```shell
curl 'PATCH -H "Authorization: <jwt token>"
-d {"name": "Team Lead", "level": "D2", "skills": [1, 3]}
http://api-gateway.andela.com/api/v1/roles/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "id": "1",
  "name": "Team Lead",
  "level": "D2",
  "skills": [
    {
      "name": "Speaking to be understood",
      "description": "should be well spoken and well articulate"
    },
    {
      "name": "Managing Expectations",
      "description": "Should be able to properly manage expectations"
    }
  ]
}
```

### HTTP Request
`PATCH http://api-gateway.andela.com/api/v1/roles/<id>`

### Url Parameters
Parameter | Description
--------- | -----------------------
id | id of the role you want to update

### Request Body

title| Description
--------- | -----------
name | name of the role
level | level of fellow that can be assigned to that role
skills | Array containing the skill id's of the skills a fellow at that role should possess

## Delete a role

This end point handles the deleting of roles

```http
DELETE /api/v1/roles/<id> HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl 'DELETE -H "Authorization: <jwt token>"
http://api-gateway.andela.com/api/v1/roles/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Role deleted"
}
```
### HTTP Request
`DELETE http://api-gateway.andela.com/api/v1/roles/<id>`

### Url Parameters
Parameter | Description
--------- | -----------------------
id | id of the role you want to delete