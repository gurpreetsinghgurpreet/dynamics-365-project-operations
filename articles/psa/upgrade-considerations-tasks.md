---
title: Upgrade considerations for the work breakdown structure
description: This article provides information about upgrading the work breakdown structure from Project Service Automation 2.x to 3.x.
ms.custom: 
  - dyn365-projectservice
ms.date: 10/18/2019
ms.topic: article
author: ruhercul
ms.author: ruhercul
audience: Admin
search.audienceType: 
  - admin
  - customizer
  - enduser
search.app: 
  - D365CE
  - D365PS
  - ProjectOperations
ms.reviewer: johnmichalak
---



# Upgrade considerations for the work breakdown structure

[!include [banner](../includes/psa-now-project-operations.md)]

This article provides information about upgrading the work breakdown structure from Project Service Automation 2.x to 3.x. This article defines the healthy state of a project in Project Service Automation (PSA) that is required for a successful upgrade. There is also information about the common blocking conditions that will cause upgrade to fail. For more information about defining project tasks and their functions within a project schedule, see [Project schedules](project-creating.md).

## Key entities
For an accurate work breakdown structure that is already loaded with resources, the following entities are required:

- [Project](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_project)
- [Project Team](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_projectteam)
- [Project Task](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_projecttask)
- [Resource Assignments](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_resourceassignment)
- [Project Task Dependency](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_projecttaskdependency)
- [Bookable Resources](/dynamics365/customerengagement/on-premises/developer/entities/bookableresource)

To define a resource loaded work breakdown structure, you must complete the following steps:

1. Create a new project. For more information about how to create a new project, see [msdyn_project](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_project).
2. Create one or more tasks. For more information about how to create a task, see [msdyn_projecttask](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_projecttask).
3. Define the task dependencies. For more information, see [Project Task Dependency](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_projecttaskdependency).
4. Assign project team members to the project. For more information, see [msdyn_projectteam](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_projectteam).
5. Assign project team members to the tasks. For more information, see [msdyn_resourceassignment](/dynamics365/customerengagement/on-premises/developer/entities/msdyn_resourceassignment).

## Project team relationships

To ensure a successful upgrade, the following relationships must be correctly maintained:
- All project team members must be associated with a bookable resource.
- All project team members must be associated with the same project. 

## Project task relationships
To ensure a successful upgrade, the following relationships must be correctly maintained:

- Any related tasks must be associated with the same project.
- Every line task must have a parent task.
- Every task must have a parent project.

### Valid conditions

- All task durations must be greater than or equal to (>=) one hour and less than 1,800,000 minutes (1,250 days).*
- All tasks must have a start date no earlier than 2000/01/01.*
- All tasks must have a start date no later than 17 years from the present day.*
- All tasks must have a start date earlier or equal to their finish date.
- All transaction types on classifications (Expense, Material, Tax, and Time) must have values for **Default Unit** and **Unit Group**.
- Date formats with letters should be avoided.

### Potential mitigation steps
- Use Advanced Find to identify Project tasks that do not contain a Project ID.
- Use Advanced Find to identify Project tasks where the scheduled duration is greater than > 1,800,000.
- Prior to making any data changes, you should investigate any customizations associated with the entity that may have led to getting the data into a bad state. These customizations should be addressed before proceeding with any data-related updates.
- For the identified tasks that have been orphaned, consider deleting these tasks if they are not needed or if they should be associated with the correct parent project.
- For any tasks where the duration is greater than 1,250 days, consider adding multiple tasks to represent the total duration, if feasible.

> [!NOTE]
> Items noted with an asterisk (\*) have limits that are due to the fact that customer relationship management (CRM) supports only 7,320 recurrence expansions. You must stay below this limit.

## Resource Assignment relationships
To ensure a successful upgrade, the following relationships must be correctly maintained:

- All Resource Assignments in a work breakdown structure must be related to the same project.
- All Resource Assignments in a work breakdown structure must be associated to project team members in the same project.

### Potential mitigation steps
- Identify all tasks that fall outside the conditions described above.  
- Any Resource Assignments that are no longer valid should be deleted.

## Project task dependency relationships
To ensure a successful upgrade, the following relationships must be correctly maintained:

- All project task dependencies must be related to the same project.
- A task can't have the same dependency referenced more than once.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
