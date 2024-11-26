---
title: Messaging for SaaS workloads on Azure
description: TBD - Messaging for SaaS workloads
author: DixitArora-MSFT
ms.author: dixitaro
ms.date: 11/26/2024
ms.topic: conceptual
---

# Messaging for SaaS workloads on Azure

- Identity is arguably the most important piece of a SaaS workload. It serves to protect tenant data from leaking across the tenant barrier. It is often overlooked or not thought of until the end of a project. Don't make that mistake.

- Understand how your tenancy model plays into identity. 
    - Tenancy model can be affected by things like: data residency requirements, compliance requirements, pricing model, and more. 
    - Having a MOBO type model could limit them from being able to use a single shared identity provider. 

## Federated Identity

- If your customer requirements dictate that you must allow them to bring their own identity provider, how you do that is important. 
- You should have a good understanding of how many identity providers you need to scale to. A solution that fits 100 unique identity providers is very different from one that fits 100,000. 
- BYOIdP gets complex and expensive. Make sure you factor that into your business model. 

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
