---
title: Messaging for SaaS workloads on Azure
description: TBD - Messaging for SaaS workloads
author: DixitArora-MSFT
ms.author: dixitaro
ms.date: 11/26/2024
ms.topic: conceptual
---

# Messaging for SaaS workloads on Azure

- SaaS applications often involve multiple microservices, external APIs, and backend systems. Messaging solution often act as a part that integrates these components, ensuring smooth and efficient operations by facilitating real-time updates and communication across these distributed systems. 

- Selecting an appropriate messaging model for multi-tenant SaaS applications is essential to enable secure, scalable, asynchronous messaging and event-driven communication. 
    - Independent software vendors (ISVs) must carefully evaluate the right messaging solution to meet the demands of a multi-tenant SaaS environment. 
    - ISVs should consider factors such as the nature of the events and messages, scalability requirements, event routing complexity, latency tolerance, and operational overhead.

## Select a messaging platform

- Choosing the right messaging service for your SaaS workload is essential, yet the variety of options available in Azure can make the decision feel overwhelming.
- The ideal service depends on factors like message type, application architecture, scalability requirements, performance needs, and tenant isolation. 
- What works best for one application might not suit another, so it’s important to align your choice with the specific messaging requirements of your workload. 

## Delegated Permissions

- A lot of end customers like to manage their own permissions/access on their end. 
- Customers should be given defined ways to do this. 
    - Via groups inherited from their side (mapping exercise and OIDC configuration is required)
    - Via a custom portal/interface the ISV builds to allow them to change permissions
    - etc

- Seat licensing is often handled through permission management. You could choose to do this as a role in your identity provider, or you could do it in the database. Make sure that if the customer has a limited number of seats, that they can't keep assigning more permissions.

## B2C vs B2B Scenarios

- The identity strategy might change depending on the type of customers you serve. You likely will not need to worry about a BYOIdP scenario in a B2C SaaS product.
- If your customers are 100% within the microsoft universe, you can rely on microsoft entra multitenant applications for a simple identity approach. 

## Cross Entra Tenant Access Management

- Guidance for reaching into the customer's entra tenant from your entra tenant. 
- Options include: service principals, lighthouse, managed applications. Discuss the pros/cons of each. 
- This should be handled with care. Only request the minimal amount of access you require from their tenant. 
