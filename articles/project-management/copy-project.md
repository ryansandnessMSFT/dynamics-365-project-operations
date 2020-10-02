---
# required metadata

title: Copy a project
description: This topic provides information about copying projects in Dynamics 365 Project Operations. 
author: ruhercul
manager: AnnBe
ms.date: 10/01/2020
ms.topic: article
ms.service: dynamics-365-customerservice
ms.reviewer: kfend 
ms.author: ruhercul
---

# Copy a project

_**Applies To:** Project Operations for resource/non-stocked based scenarios, Lite deployment - deal to proforma invoicing_

With Dynamics 365 Project Operations, you can quickly build new projects by using the **Copy Project** action on the **Projects** from. To copy a project, select a project, and then select **Copy**. The action will copy:

- Project properties
- The Work breakdown structure
- Project team members
- Project estimates
- Project expense estimates

## Project properties

When the project is copied, the values in the following fields are copied:

- Name
- Description
- Customer
- Calendar Template
- Currency
- Contracting Unit
- Project Manager
- Status
- Overall Project Status
- Comments
- Estimates
- Estimated Start Date
- Finish Date
- Effort (Hours)
- Estimated Labor Cost
- Estimated Expense Cost

## Work breakdown structure

When the project is copied, the entire resource-loaded work breakdown structure is copied. Named resources are replaced with generic resources. If the named resources don't have the same working hours as the generic resource, the schedule will be recalculated and task durations may change.

## Project team members

When a project team is copied from the source project, the generic resources are copied. Generic resource assignments are also maintained as they were in the source project. Named resources will be converted to generic team members.

## Estimates

When the project is copied, both resource and expense estimate lines are copied from the source project.