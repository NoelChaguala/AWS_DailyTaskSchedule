# Test Plan and Results

## Overview

This document describes the test scenarios used to evaluate the AWS PartyRock Daily Task Scheduler.

Testing focuses on scheduling accuracy, task prioritization, workload feasibility, constraint handling, consistency across outputs, and the usefulness of generated recommendations.

## Test Environment

**Application:** AWS PartyRock Daily Task Scheduler

**Testing approach:** Manual functional testing using defined inputs and expected outcomes.

**Primary test scenario:** An overloaded day with four tasks totaling eight hours of work.

## Test Case 1: Overloaded Workload

**Objective:** Verify that the application identifies when the requested workload exceeds the available time.

### Input

| Setting             | Value                    |
| ------------------- | ------------------------ |
| Day Start Time      | 9:00 AM                  |
| Day End Time        | 1:00 PM                  |
| Available Window    | 4 hours                  |
| Lunch Window        | 11:00 AM–11:30 AM        |
| Break Duration      | 10 minutes               |
| Break Frequency     | Every 60 minutes of work |
| Reserve Buffer Time | Yes                      |
| Buffer Duration     | 15 minutes               |
| Scheduling Strategy | Balanced Productivity    |

### Tasks

| Task                           | Priority | Duration    | Deadline    |
| ------------------------------ | -------- | ----------- | ----------- |
| Finish programming assignment  | High     | 2 hours     | Today       |
| Study for calculus exam        | High     | 3 hours     | Tomorrow    |
| Complete project documentation | Medium   | 2 hours     | No deadline |
| Respond to emails              | Low      | 1 hour      | No deadline |
| **Total**                      |          | **8 hours** |             |

### Expected Results

The application should identify the workload as **Overloaded** because eight hours of tasks cannot fit into the available four-hour window.

It should account for lunch, breaks, and buffer time when calculating capacity. It should prioritize the programming assignment because it is high priority and due today, followed by calculus study because it is high priority and due tomorrow.

Lower-priority tasks without deadlines should generally be deferred before the urgent tasks.

### Validation

- [x] Overloaded status returned.
- [x] Total task duration correctly identified as eight hours.
- [x] Priority order reflected task priorities and deadlines.
- [x] Rescheduling recommendations were provided.
- [x] Lunch, breaks, and buffer time were considered.

**Result:** Passed for the tested behavior.

## Test Case 2: Priority Analysis

**Objective:** Verify that tasks are ranked according to the selected strategy and supplied task information.

### Expected Results

The output should rank the tasks in the following order:

1. Finish programming assignment.
2. Study for calculus exam.
3. Complete project documentation.
4. Respond to emails.

The output should explain why the tasks are ordered this way without independently calculating whether the workload fits or recommending which tasks to defer.

### Validation

- [x] Tasks ranked by priority and deadlines.
- [x] Reasoning provided for the task order.
- [x] No unsupported dependencies invented.
- [x] Selected scheduling strategy used consistently.
- [x] Total task duration correctly identified as eight hours.

**Result:** Passed for the tested behavior.

## Test Case 3: Daily Schedule

**Objective:** Verify that the generated schedule respects time boundaries and scheduling constraints.

### Expected Results

The schedule should:

- Remain within 9:00 AM–1:00 PM.
- Respect the 11:00 AM–11:30 AM lunch window.
- Include the required breaks.
- Account for the 15-minute buffer.
- Avoid overlapping activities.
- Preserve stated task durations rather than silently shortening them.
- Identify tasks that cannot fit in a separate section.

### Validation

- [ ] Confirmed no overlapping entries.
- [ ] Confirmed all scheduled activities remain within the time window.
- [ ] Confirmed lunch and breaks are respected.
- [ ] Confirmed buffer time is accounted for.
- [ ] Confirmed unscheduled tasks are identified.

**Result:** Complete this checklist after reviewing the generated schedule.

## Test Case 4: Productivity Recommendations

**Objective:** Verify that recommendations are practical and consistent with the schedule and feasibility assessment.

### Expected Results

The output should recommend realistic adjustments, protect time for urgent work, and suggest when lower-priority tasks can be rescheduled.

It should not contradict the feasibility result or simply repeat the entire schedule.

### Validation

- [x] Recommendations reflect the workload and priorities.
- [x] Recommendations respect the available time.
- [x] Deferred tasks are identified consistently.
- [x] No unsupported task details are introduced.

**Result:** Complete this checklist after reviewing the generated recommendations.

## Test Case 5: End-of-Day Checklist

**Objective:** Verify that the checklist accurately represents planned, outstanding, and deferred work.

### Expected Results

The output should provide actionable checklist items based on the generated schedule and available task information.

It should not mark tasks as completed without confirmation or invent additional tasks.

### Validation

- [x] Checklist items correspond to the provided tasks.
- [x] Deferred tasks remain identifiable.
- [x] No task is incorrectly marked completed.
- [x] Checklist aligns with the schedule and feasibility assessment.

**Result:** Complete this checklist after reviewing the generated checklist.

## Test Case 6: Feasible Workload

**Objective:** Verify that the application can identify a workload that fits within the available time.

### Suggested Input

| Setting             | Value                       |
| ------------------- | --------------------------- |
| Day Start Time      | 9:00 AM                     |
| Day End Time        | 5:00 PM                     |
| Task                | Complete a short assignment |
| Task Duration       | 30 minutes                  |
| Reserve Buffer Time | No                          |

Use reasonable break and lunch preferences for the test.

### Expected Results

The application should identify the workload as **Feasible** if the task and all required scheduling activities fit within the available window.

**Result:** Pending test.

## Test Case 7: Missing or Invalid Time Information

**Objective:** Verify that the application identifies invalid scheduling inputs.

### Suggested Scenarios

- Missing day start time.
- Missing day end time.
- End time earlier than start time.
- Missing task durations when duration is required.
- Fixed commitments that overlap each other.

### Expected Results

The application should clearly explain the invalid or missing information and request clarification instead of presenting an unreliable schedule or feasibility status.

**Result:** Pending test.

## Test Case 8: Cross-Output Consistency

**Objective:** Verify that all five outputs use compatible scheduling assumptions and task information.

### Expected Results

- Priority Analysis establishes the task ordering.
- Feasibility Check evaluates the available capacity.
- Daily Schedule respects the same constraints and identifies tasks that cannot fit.
- Productivity Recommendations agree with the feasibility assessment.
- End-of-Day Checklist reflects planned and deferred work.

**Result:** Review after all outputs have been generated using the same inputs.

## Summary

The initial overloaded-workload and priority-analysis scenarios have been tested successfully. The remaining test cases provide a checklist for validating the Daily Schedule, Productivity Recommendations, End-of-Day Checklist, input validation, and consistency across the complete workflow.

Testing should be repeated whenever prompts or application inputs are changed.
