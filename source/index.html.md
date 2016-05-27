---
title: Andela API Gateway

language_tabs:
  - http
  - shell

includes:
  - api/roles
  - api/assessment
  - api/authentication
  - errors

search: true
---

# Introduction

Welcome to Andela's API gateway. This api gateway is the single entry point into all andela's microservices systems.

# Authentication

This API gateway uses JWT tokens to allow access to the API. A user receives a JWT token upon authentication through his andela google account.

The JWT token is expected to be included in all API requests to the API gateway in the header.

`Authorization: <jwt token>`