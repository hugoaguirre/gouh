+++
title = 'SD: API Gateway'
date = 2024-10-09T12:26:33-06:00
draft = false
+++

An API Gateway is an intermediary between clients and backend services, microservices or APIs.

It's purpose is to provide a single entry point for external customers to access the services in the backend.

Below, there will be sections explaining the API Gateway responsibilities

## Routing

Client request is received and forwarded to the appropriate microservice.

## Rate limiting and throttling

API Gateway can set a limit on the numbers of requests a client makes, thus, preventing DDoS attacks.

## Caching

Some backend responses can be cached in the API Gateway, this will help in reducing the amount of requests done to the microservices.

## Authentication and Authorization

The API Gateway can enforce access control policies to force client authentication so only authorized users can access the microservices.

## Load Balancing

As mentioned in the Load Balancing post, the requests gets evenly distributed among multiple instances of microservices to reduce heavy loads and saturation.

## Monitoring

Metrics and data collection from microservices to identify and diagnose problems.

## Data Transformation

Server responses could be transformed to the appropriate format (such as JSON or XML) or even collecting responses from multiple microservices and returning a single response to the client.

## Circuit Breaker

The API Gateway could be used to implement a [Circuit Breaker](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern) pattern to identify failing microservices and prevent a cascading failure in the system.

## Service Discovery

The API Gateway can be used to discover the available microservices making it easier to add new microservices or make changes to the existing ones without impacting the clients.

## API Versioning

It can maintain multiple API Versions so clients don't get impacted with new changes while allowing developers to add new changes to the API

## Error Handling

Pretty useful when the backend services are not available or return unexpected errors. The API Gateway can provide consistent responses.

## Web Application Firewall (WAF)

Firewall to protect backend services from common web-based threats, such as SQL injections, cross-site scripting, or DDoS attacks.

## API Documentation

The API Gateway can generate and serve API documentation with the standard formats (Swagger or OpenAPI)

# Cons of using an API Gateway

The previous list of features could be understood as the pros of using API Gateways on your system architecture but, what about the cons?

- Complexity
- Single point of failure
- Cost
- Vendor lock-in
- Latency

# What's the difference between a LB and an API Gateway?

API Gateway **routes** requests to the appropriate microservice
Load Balancer **distributes** the requests evenly across a group of backend servers
