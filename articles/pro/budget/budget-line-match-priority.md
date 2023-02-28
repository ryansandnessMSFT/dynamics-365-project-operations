---
title: Budget line match priority
description: This article explains how budget line match priority works for project budgets.
author: niranjanmaski
ms.date: 01/13/2023
ms.topic: article
ms.reviewer: johnmichalak
ms.author: nimaski
---

# Budget line match priority

**_Applies to:_** _Lite deployment - deal to proforma invoicing._

Budget line match priority defines the order in which an actual is matched against the different dimensions of budget lines.

As part of the solution update that includes project budgeting, the Budget line match priority table is created in the solution.

You enable the project cost budget feature by using a feature flag. For more information, see [Enable the project cost budget feature](create-delete-project-budget.md#enable-the-project-cost-budget-feature).

> [!NOTE]
> After the project budget feature is enabled in an organization, it can't be disabled. However, you don't have to create a budget for every project.

After the feature flag is enabled, the **Budget match priorities** tab should appear on the project parameters main page. This tab shows the following default rows that are applicable for the **Time**, **Expense**, and **Material** transaction classes in the context of a class.

| Field name | Applicable transaction class | Context | Budget match priority |
|---|---|---|---|
| msdyn\_transactioncategory | Expense | Cost | 1 |
| msdyn\_task | Expense | Cost | 2 |
| msdyn\_costtype | Expense | Cost | 3 |
| msdyn\_accountvendor | Expense | Cost | 4 |
| msdyn\_product | Material | Cost | 1 |
| msdyn\_writeinproductdescription | Material | Cost | 2 |
| msdyn\_task | Material | Cost | 3 |
| msdyn\_costtype | Material | Cost | 4 |
| msdyn\_accountvendor | Material | Cost | 5 |
| msdyn\_resourcecategory | Time | Cost | 1 |
| msdyn\_resourceorganizationalunitid | Time | Cost | 2 |
| msdyn\_bookableresource | Time | Cost | 3 |
| msdyn\_task | Time | Cost | 4 |
| msdyn\_costtype | Time | Cost | 5 |
| msdyn\_accountvendor | Time | Cost | 6 |

## How does budget match priority work?

Time entry, expense entry, or material use is submitted against a project for approval. After it's approved, it's considered an approved actual that's used in project cost budgeting calculations.

Actuals have dimensions that define an actual. Here are some examples:

- The task that the actual is created against
- The role of the resource that's submitting the time entry
- The name of the material that's used
- A flight expense that's billed against a project
- A time entry from a subcontractor that's approved by a project manager

When actuals are posted against a project, they must be mapped to the correct budget lines. This mapping is done by matching the dimensions of incoming actuals with the dimensions of all budget lines in the cost budget. An actual is matched to the budget line that matches most of its dimensions.

During matching, the order that the matching algorithm works in is defined by the Budget line match priority table.

Priority 1 is the highest priority for dimensions of a transaction class. The algorithm tries to match all dimensions of an actual against all budget lines.

If no match is found, and no error is encountered, the matching algorithm avoids the *lowest-priority dimension*, according to the Budget line match priority table, and tries to match again. This process continues until either a match is found or an error is encountered. If more than one budget line matches an actual, this situation is also considered an error.

### Example

This example shows how the process works for an expense that's posted against a project. The following table shows the priority order in which the actual is matched for an expense if the default budget match priority is used.

| Field name | Applicable transaction class | Context | Budget match priority |
|---|---|---|---|
| msdyn\_transactioncategory | Expense | Cost | 1 |
| msdyn\_task | Expense | Cost | 2 |
| msdyn\_costtype | Expense | Cost | 3 |
| msdyn\_accountvendor | Expense | Cost | 4 |

The actual expense is matched to the budget line where the largest number of dimensions is matched.

1. The matching algorithm tries to match a budget line where **msdyn\_transactioncategory**, **msdyn\_task**, **msdyn\_costtype**, and **msdyn\_accountvendor** are defined.
1. If there's no match, the lowest-priority dimension, **msdyn\_accountvendor**, is avoided in the next attempt to match against a budget line.
1. If there still is no match, the next-lowest-priority dimension, **msdyn\_costtype**, is avoided in the next attempt to match against a budget line.
1. The process continues until a unique budget line is matched or an error is encountered.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

[Microsoft](https://www.microsoft.com)