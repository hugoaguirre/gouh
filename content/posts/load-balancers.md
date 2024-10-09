+++
title = 'SD: Load Balancers'
date = 2024-10-08T21:53:16-06:00
draft = false
+++

Load Balancers (LB) are a crucial component for System Design. They are basically in charge of distributing incoming requests and traffic _evenly_ across multiple servers while avoiding the overload and downtime of servers.

## Good places to put a LB

- Between user and web servers
- Between web servers and internal platform layer
- Between platform layer and databases

## How does a request get processed by a Load Balancer?

- Request is received
- Request then is evaluated:
  - LB determines which server or resource should handle the request
    - At this point, the Load Balancer Algorithm takes into account the following things:
      - Server capacity and response time
      - Number of active connections
      - Geographic location

- LB forwards request to the server
- Server responds back to the LB
- LB processes response and sends it back to the user/client

## Load Balancer Algorithms

The algorithms listed here will be a good option in particular scenarios.

In general, these algorithms will ensure efficient utilization of available resources, improve overall system performance and maintain high availability and reliability.

### Round Robin

Assigns incoming requests to servers in a cyclic order by following the [Round Robin technique](https://en.wikipedia.org/wiki/Round-robin_item_allocation).

#### Uses

- Suitable for environments where _**all servers have similar capacity and performance**_
- Good option for _**stateless**_ applications where each request can be handled independently

### Least Connections

Assigns incoming requests to the server with fewest active connections at the time of the request

#### Uses

- Suitable for environments where _**servers have different capacity and workload**_
- Good option for _**stateful**_ applications where maintaining the session state is mandatory
- When traffic is highly variable and unpredictable
