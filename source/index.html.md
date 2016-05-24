---
title: Andela API Gateway

language_tabs:
  - http
  - shell

includes:
  - errors

search: true
---

# Introduction

Welcome to Andela's API gateway. This api gateway is the single entry point into all andela's microservices systems.

# Authentication

This API gateway uses JWT tokens to allow access to the API. A user receives a JWT token upon authentication through his andela google account.

The JWT token is expected to be included in all API requests to the API gateway in the header.

`Authorization: <jwt token>`

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
  "name": <role name>,
  "level": <fellow level>,
  "skills": <array of skills id>
}
```

```shell
curl 'POST -H "Authorization: <jwt token>"
-d {"name": <role name>, "level": <fellow level>, "skills": <array of skills id>}
http://api-gateway.andela.com/api/v1/roles/'
```

> The above command returns JSON structured like this:

```json
{
  "id": "<role id>",
  "name": "<role name>",
  "level": "<role level>",
  "skills": [
    {
      "name": "<skill_1 name>",
      "description": "<skill_1 description>"
    },
    {
      "name": "<skill_2 name>",
      "description": "<skill_2 description>"
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
  "name": <role name>,
  "level": <fellow level>,
  "skills": <array of skills id>
}
```

```shell
curl 'PATCH -H "Authorization: <jwt token>"
-d {"name": <role name>, "level": <fellow level>, "skills": <array of skills id>}
http://api-gateway.andela.com/api/v1/roles/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "id": "<role id>",
  "name": "<role name>",
  "level": "<role level>",
  "skills": [
    {
      "name": "<skill_1 name>",
      "description": "<skill_1 description>"
    },
    {
      "name": "<skill_2 name>",
      "description": "<skill_2 description>"
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

#Assessment Microservice

### Overview
This microservice handles the creating, deleting, updating and fetching of Skills, Scores and Scoreguidelines for Andela fellows.

## Get All Skills
```http
GET /api/v1/skills HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/skills"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Reading to be understood",
    "type": "SOFT"
  },
  {
    "id": 2,
    "name": "Writing professionally",
    "type": "SOFT"
  },
  {
    "id": 3,
    "name": "Managing Expectations",
    "type": "SOFT"
  }
]
```

This endpoint retrieves all skills.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/skills`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 1 | Helps paginate the collection.
limit | 10 | returns the first ten records of a particular page


## Get a Specific Skill

```http
GET /api/v1/skills/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
 http://api-gateway.andela.com/api/v1/skills/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 5,
  "name": "Reading to be understood",
  "type": "SOFT"
}
```

This endpoint retrieves a single skill.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/skill/<id>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The id of the skill to be retrieved


## Create a skill

```http
POST /api/v1/skills HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "name": "<skill name>",
  "type": "<skill type>"
}
```

```shell
curl 'POST -H "Authorization: <jwt token>"
-d {"name": <skill name>, "type": <skill type>}
http://api-gateway.andela.com/api/v1/skills/'
```

> The above command returns JSON structured like this:

```json
{
  "name": "<skill name>",
  "type": "<skill type>"
}
```

This end point creates a new skill

### HTTP Request
`POST http://api-gateway.andela.com/api/v1/skills`

### Request Body

title| Description
--------- | -----------
name | name of the skill
type | the type of skill being created (SOFT or TECH)


## Update a skill

This end point updates an existing skill

```http
PATCH /api/v1/skills/<id> HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "name": <skill name>,
  "type": <skill type>,
}
```

```shell
curl 'PATCH -H "Authorization: <jwt token>"
-d {"name": <skill name>, "type": <skill type>}
http://api-gateway.andela.com/api/v1/skills/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "name": "<skill name>",
  "type": "<skill type>"
}
```

### HTTP Request
`PATCH http://api-gateway.andela.com/api/v1/skills/<id>`

### Url Parameters
Parameter | Description
--------- | -----------------------
id | id of the skill you want to update

### Request Body

title| Description
--------- | -----------
name | name of the skill
type | type of skill (SOFT or TECH)

## Delete a skill

This end point handles the deleting of skills

```http
DELETE /api/v1/skills/<id> HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl 'DELETE -H "Authorization: <jwt token>"
http://api-gateway.andela.com/api/v1/skills/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Skill deleted"
}
```
### HTTP Request
`DELETE http://api-gateway.andela.com/api/v1/skills/<id>`

### Url Parameters
Parameter | Description
--------- | -----------------------
id | id of the skill you want to delete

<!----- new stuff ---->
## Get All scoreguidelines
```http
GET /api/v1/scoreguidelines HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
http://api-gateway.andela.com/api/v1/scoreguidelines"
```

> The above command returns JSON structured like this:

```json
[

    {
      "id": 1,
      "level": "D1",
      "score": 3,
      "description": "Fellow can do whatever",
      "skill_id": 5,
      "skill": {
        "id": 5,
        "name": "Reading to be understood",
        "type": "SOFT"
      }
    }, {
      "id": 2,
      "level": "D0B",
      "score": 3,
      "description": "Fellow can do whatever",
      "skill_id": 5,
      "skill": {
        "id": 5,
        "name": "Reading to be understood",
        "type": "SOFT"
      }
    }
]
```

This endpoint retrieves all scoreguidelines.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/scoreguidelines`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 1 | Helps paginate the collection.
limit | 10 | returns the first ten records of a particular page


## Get a Specific scoreguideline

```http
GET /api/v1/scoreguidelines/<id> HTTP/1.1
Accept: */*
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl "GET -H 'Authorization: <jwt token>'
 http://api-gateway.andela.com/api/v1/scoreguidelines/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "level": "D1",
  "score": 3,
  "description": "Fellow can do whatever",
  "skill_id": 5,
  "skill": {
    "id": 5,
    "name": "Reading to be understood",
    "type": "SOFT"
  }
}
```

This endpoint retrieves a single score guideline.

### HTTP Request

`GET http://api-gateway.andela.com/api/v1/scoreguidelines/<id>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The id of the scoreguideline to be retrieved


## Create a scoreguideline

```http
POST /api/v1/scoreguidelines HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "level": "<new level>",
  "score": "<new score>",
  "description": "<new description>",
  "skill_id": "<new skill>"
}
```

```shell
curl 'POST -H "Authorization: <jwt token>"
-d {level": "<new level>", "score": "<new score>",
  "description": "<new description>",
  "skill_id": "<new skill>"}
http://api-gateway.andela.com/api/v1/scoreguidelines
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "level": "<new level>",
  "score": "<new score>",
  "description": "<new description>",
  "skill_id": "<new skill>"
}
```

This end point creates a new score guideline.

### HTTP Request
`POST http://api-gateway.andela.com/api/v1/scoreguidelines`

### Request Body

title| Description
--------- | -----------
level | level of fellow for particular scoreguideline
score | score for scoreguideline
description | description of scoreguideline
skill_id | skill id of the particular guideline


## Update a scoreguideline

This end point updates an existing score guideline

```http
PATCH /api/v1/scoreguidelines/<id> HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
Body: {
  "level": "<new level>",
  "score": "<new score>",
  "description": "<new description>",
  "skill_id": "<new skill>"
}
```

```shell
curl 'PATCH -H "Authorization: <jwt token>"
-d {level": "<new level>", "score": "<new score>",
  "description": "<new description>",
  "skill_id": "<new skill>"}
http://api-gateway.andela.com/api/v1/scoreguidelines/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "level": "<new level>",
  "score": "<new score>",
  "description": "<new description>",
  "skill_id": "<new skill>"
}
```

### HTTP Request
`PATCH http://api-gateway.andela.com/api/v1/scoreguidelines/<id>`

### Url Parameters
Parameter | Description
--------- | -----------------------
id | id of the scoreguideline you want to update

### Request Body

title| Description
--------- | -----------
level | level of fellow for particular scoreguideline
score | score for scoreguideline
description | description of scoreguideline
skill_id | skill id of the particular guideline

## Delete a scoreguideline

This end point handles the deleting of score guidelines.

```http
DELETE /api/v1/scoreguidelines/<id> HTTP/1.1
Accept: */*
Content-type: application/x-www-form-urlencoded
Authorization: <jwt token>
Host: api-gateway.andela.com
```

```shell
curl 'DELETE -H "Authorization: <jwt token>"
http://api-gateway.andela.com/api/v1/scoreguidelines/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Scoreguideline deleted"
}
```
### HTTP Request
`DELETE http://api-gateway.andela.com/api/v1/scoreguidelines/<id>`

### Url Parameters
Parameter | Description
--------- | -----------------------
id | id of the scoreguideline you want to delete
