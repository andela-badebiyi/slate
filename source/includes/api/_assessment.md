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
  "name": "Object oriented programming",
  "type": "TECH"
}
```

```shell
curl 'POST -H "Authorization: <jwt token>"
-d {"name": "Object oriented programming", "type": "TECH"}
http://api-gateway.andela.com/api/v1/skills/'
```

> The above command returns JSON structured like this:

```json
{
  "name": "Object oriented programming",
  "type": "TECH"
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
  "name": "Adaptability",
  "type": "SOFT",
}
```

```shell
curl 'PATCH -H "Authorization: <jwt token>"
-d {"name": "Adaptability", "type": "SOFT"}
http://api-gateway.andela.com/api/v1/skills/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "name": "Adaptability",
  "type": "SOFT"
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
  "level": "D3",
  "score": 2,
  "description": "should be averagely proficient in this skill",
  "skill_id": 23
}
```

```shell
curl 'POST -H "Authorization: <jwt token>"
-d {level": "D3", "score": 2,
  "description": "should be averagely proficient in this skill",
  "skill_id": 23}
http://api-gateway.andela.com/api/v1/scoreguidelines
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "level": "D3",
  "score": 2,
  "description": "should be averagely proficient in this skill",
  "skill_id": 23
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
  "level": "D3",
  "score": 2,
  "description": "should be averagely proficient in this skill",
  "skill_id": 23
}
```

```shell
curl 'PATCH -H "Authorization: <jwt token>"
-d {level": "D3", "score": 2,
  "description": "should be averagely proficient in this skill",
  "skill_id": 23}
http://api-gateway.andela.com/api/v1/scoreguidelines/<id>'
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "level": "D3",
  "score": 2,
  "description": "should be averagely proficient in this skill",
  "skill_id": 23
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