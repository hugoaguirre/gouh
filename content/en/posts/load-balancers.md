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

1. Request is received
2. Request then is evaluated:

  LB determines which server or resource should handle the request using a balancing algorithm taking in consideration the following things:  
    - Server capacity and response time
    - Number of active connections
    - Geographic location
3. LB forwards request to the server
4. Server responds back to the LB
5. LB processes response and sends it back to the user/client

## Load Balancer Algorithms

The algorithms listed here will be a good option in particular scenarios.

In general, these algorithms will ensure efficient utilization of available resources, improve overall system performance and maintain high availability and reliability.

### Round Robin

Assigns incoming requests to servers in a cyclic order by following the [Round Robin technique](https://en.wikipedia.org/wiki/Round-robin_item_allocation).

Use cases:

- Suitable for environments where _**all servers have similar capacity and performance**_
- Good option for _**stateless**_ applications where each request can be handled independently

### Least Connections

Assigns incoming requests to the server with fewest active connections at the time of the request

Use cases:

- Suitable for environments where _**servers have different capacity and workload**_
- Good option for _**stateful**_ applications where maintaining the session state is mandatory
- When traffic is highly variable and unpredictable

### Weighted Round Robin

Assigns weights to each server based on their capacity or performance.
It basically ensures that more powerful servers handle a larger share of the load.

Use cases:

- Environments where servers have different processing capabilities
- Useful in database clusters where some nodes have higher processing power and can handle more queries

### Weighted Least Connections

Combines Least Connections and Weighted Round Robin algorithms.
Takes into account the following things:

- Current server load (# active connections)
- Relative capacity of each server (weight)

Proportionally distributes larger shares of the load to most powerful servers and also it dynamically adjusts real-time load on each server.

Use cases:

- Environments where servers have different processing capabilities
- Applications with variable traffic patterns, ensuring no single server becomes a bottleneck
- Useful in database clusters where nodes have varying performance capabilities and query loads

### IP Hash

Converts the IP into a hash value and then (based on the hash value) the LB will determine which server should handle the request.

Ensures requests are consistently routed to the same server, providing session persistence.

Use cases:

- Geographically distributed clients (on different regions) and consistent routing is required
- Applications where maintaining the session persistence is mandatory (e.g. Shopping Carts or User Sessions)
