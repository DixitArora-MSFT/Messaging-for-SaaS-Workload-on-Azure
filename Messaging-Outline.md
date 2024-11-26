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

## Tenancy model and isolation

- Most SaaS providers host messaging resources on behalf of their customers, allowing greater flexibility in service design. Ensure robust workload isolation to optimize costs while maintaining performance and seamless customer experience.
   
- ISVS should be given defined ways to do this. 
    - Guidance on evaluate the isolation features of the messaging services to ensure that it meets ISVs tenancy model requirements.
    - Guidance on choosing the right tenacy model by keeping balance between cost and customer experince.

## Scale and cost 

- The identity strategy might change depending on the type of customers you serve. You likely will not need to worry about a BYOIdP scenario in a B2C SaaS product.
- If your customers are 100% within the microsoft universe, you can rely on microsoft entra multitenant applications for a simple identity approach. 

## Resiliency and reliability 

- Guidance for reaching into the customer's entra tenant from your entra tenant. 
- Options include: service principals, lighthouse, managed applications. Discuss the pros/cons of each. 
- This should be handled with care. Only request the minimal amount of access you require from their tenant. 
