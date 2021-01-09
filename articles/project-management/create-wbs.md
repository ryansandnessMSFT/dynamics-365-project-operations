--- 

title: Create a work breakdown structure 
description: This topic explains how to create a work breakdown structure (WBS) inclusive of the basic controls in the new scheduling interface.
author:  ruhercul
manager: tfehr 
ms.date: 01/07/2021  
ms.topic: article 
ms.service: project-operations 
ms.reviewer: kfend 
ms.author: ruhercul
--- 

# Create a work breakdown structure (WBS)

A project schedule communicates what work must be completed, which resources will do the work, and the timeframe in which the work must be completed. The schedule reflects all the work associated with delivering the project on time. In Dynamics 365 Project Operations, you create a project schedule by:

  - Breaking the work down into manageable tasks.
  - Estimating the time that is required to do each task.
  - Setting task dependencies.
  - Setting task durations.
  - Estimating the generic resources that will do the tasks. 

The project schedule is created on the **Schedule** tab on the **Project** page.

## Tasks

The first step in creating a project schedule is to break the work down into manageable portions. The schedule in Project Operations supports the following features:

- Summary or container tasks
- Leaf node tasks

### Summary tasks

Summary tasks can store other summary tasks or leaf node tasks. They have no work effort or cost of their own. Instead, their work effort and cost are a rollup of the work effort and cost of their container tasks. The start date of the summary task is the start date of the container tasks, and the end date is the end date of the container tasks. The name of a summary task can be edited, but scheduling properties, including effort, dates, and duration, can't be edited. If you delete a summary task, you also delete all its container tasks.

### Leaf node tasks

Leaf node tasks represent the most granular work on the project. They have an estimated effort, resources, planned start and end dates, and a duration.

## Create a task hierarchy

### Add a task

Complete the following steps to add one or more tasks.

1. Go to **Projects** and select and open the project record for which you want to create a schedule. 
2. Select the **Tasks** tab. 
3. Select **Add new task**, enter a name for the task, and then press Enter.
2. Enter another task name and press Enter again until you have a full list of tasks.

### Manage hierarchy of a task

When a task is indented, it becomes a child of the task that is directly above it. The schedule ID of the task is then recalculated so that it's based on the schedule ID of its new parent and follows the outline numbering scheme. The parent task is now a summary task. Therefore, it becomes a rollup of its child tasks. When a task is promoted, it's no longer a child of the task that was its parent. The schedule ID is then recalculated so that it reflects the task's updated depth and position in the hierarchy. The effort, cost, and dates of the previous parent task are recalculated so that they don't include this task.

Complete the following steps to indent or promote a task.

1. On the **Project** page, on the **Tasks** tab, under **Summary tasks**, select the three vertical dots by the task name, and then select **Make subtask**. 
2. Select the task to indent or promote. To select more than one task, select a task, press and hold Ctrl, and then select additional tasks.
2. Select **Indent** or **Promote subtask**  to move tasks under or out from under summary tasks.

### Move tasks up and down

Tasks can me moved to any level in the work breakdown structure in one of two ways:

- Select one more tasks and drag them to the desired location.
- Select one or more tasks, right-click and select **Cut**, select the destination cell in the schedule, and then right-click and select **Paste**.

## Task attributes

A task's name describes the work that must be completed. In Project Operations, the attributes associated with a task describe the schedule of the task and its staffing requirements.

## Schedule attributes

The **Effort**, **Start date**, **End date**, and **Duration** attributes define the schedule for the task.

The following table shows additional schedule attributes.

| **Final display name** | **Final description** |
| --- | --- |
| Effort Completed (Hours) | Completed work for the task in hours. |
| Duration | Displays the duration in days for the task. |
| Total Effort | Total work for the task in hours. |
| Finish | Finish date and time. |
| % Complete | The percentage of the task that is complete. |
| Project Bucket | The task board can be grouped by bucket so each bucket has its own column. |
| Effort Remaining (Hours) | The remaining work for the task in hours. |
| Start | Start date and time. |
| Name | The name of the task. |
| ID | The ID of the task in the work breakdown structure. |

## Staffing attributes

Staffing attributes are accessed through the **Resources** field in the schedule. You can either search for an existing resource, or select **Create**, and in the **Quick Create** pane, add a project team member as a new resource.

The **Role**, **Resourcing Unit**, and **Position Name** fields are used to describe the staffing requirements for the task. These staffing attributes, together with the task schedule are used to find available resources to do this task.

   - **Role**: Specify the type of resource that is required to do the task.
   - **Resourcing unit**: Specify the unit that resources for the task should be assigned from. This attribute affects the cost and sales estimate for the task if the cost and bill rate for the resource are set based on resourcing units.
   - **Position name**: Enter a name for the generic resource that serves as a placeholder for the resource that will ultimately do the work.

The **Resources** field holds the position name of the generic resource or named resource when one is found.

The **Category** field holds the values that indicate a broader type of work that the task can be grouped into. This field doesn't affect scheduling or staffing. Instead, the field is used only for reporting.

## Task dependencies

You can use the schedule in Project Operations to create predecessor relationships between tasks. The **Predecessor** field uses one or more values to indicate the tasks that a task depends on. When predecessor values are assigned to a task, the task can start only after all of the predecessor tasks have been completed. Because of the dependency, the planned start date of the task is reset to the date when the predecessor tasks are completed.

The task mode has no effect on updates that are made to the start and end dates of predecessor/dependent tasks.

## Accessibility and keyboard shortcuts

The **Schedule** grid is fully accessible and can be used with screen readers such as Narrator, JAWS, or NVDA. You can move through the grid area by using arrow keys (as in Microsoft Excel), you can use the Tab key to advance through the interactive user interface elements, and you can use the Down arrow key, the Enter key, or the Spacebar to select and open the drop-down menus.