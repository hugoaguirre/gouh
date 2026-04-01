+++
title = 'SD: System Design Interview'
date = 2026-04-01T10:26:33-06:00
draft = false
+++

# System Design Interview

## What to expect from a System Design Interview?

A System Design Interview (SDI) is an assessment that tests the candidate's
ability to design and understand complex and large-scale software systems.

Candidates must keep in mind that System Design problems do not have an absolute
answer and they are expected (by the interviewers) to decompose the problem into
small pieces to understand the candidate's problem solving skills.

SDI are full of trade-offs, no answer is correct but the expectation is that
the candidate should understand the impact of those trade-offs.

### How you should structure your next SDI?

Most of the time the System Design Interviews are a single vague, unclear
open-ended question; e.g.: "Design a booking system for a parking lot",
then, the candidate is expected to break that open-ended question into small
pieces so the problem starts to make sense.

As a rule of thumb, you can structure your SDI by following the next steps:

1. Clarify Requirements
2. Estimate Scale (back of the envelope estimations)
3. Define your API interfaces
4. Data modeling
5. Design the high level architecture diagram
6. Detailed design
7. Identify and resolve bottlenecks

Below you can find a small description of the expectation on every step:

| Step                             | Expectations                                                          | Considerations                                                                          |
| -------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Clarify Requirements             | Candidates must identify Functional and Non-Functional requirements   | FR: What are the core features? NFR: How many requests per second must it handle?       |
| Estimate Scale                   | Determine the expected load on the system by doing rough calculations | Estimate traffic volume, storage, bandwidth, resources, latency                         |
| Define API interfaces            | Define 2 or 3 APIs upon agreement with the interviewer                | What would be the most important API calls in your system? How does the data look like? |
| Data modeling                    | Determine the schema of your data. Relations between entities         | SQL or NoSQL? How to store media files? Are you considering indexes? Sharding?          |
| High level architecture diagram  | Birds eye view of the system. Outline clients, servers, db, cache     | Ensure you have components that handle each major function                              |
| Detailed design                  | Dig deeper into 2 or 3 components of your design                      | Wait for interviewer feedback and make sure to present trade-offs                       |
| Identify and resolve bottlenecks | Find bottlenecks in your design, discuss them                         | Is there any point of failure in our system? How are we monitoring performance?         |

## 1. Requirements

This could be one of the most important parts during the System Design Interview
since a vague or wrong definition of requirements could lead to changes in the
final architecture

As we mentioned above, in this first part of the interview, we should identify
_Functional and Non-Functional requirements_ which are defined as follows:

### Functional Requirements

A proper identification of Functional Requirements indicates a strong understanding
of how the system should behave. In other words, they describe the various functions
the system must perform.

[!NOTE]
Functional Requirements often form the backbone of your system design

### Non-Functional Requirements

These requirements answer the following question: _How the system performs a task?_
To get a better understanding of what kind of requirements should be tagged as
non-functional, you can focus on the _quality_ attributes of the system.

- Scalability: Handle growth in users or data
- Performance: Handle concurrency, high latency and process transactions.
- Security: Handle sensitive data
- Availability: The system should be up and running a defined percentage of time

## 2. Rough estimations (back of the envelope estimations)

## 3. System interface definitions

## 4. Data modeling

## 5. High level design

## 6. Detailed design

## 7. Identify and resolve bottlenecks
