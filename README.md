# AWS PartyRock Daily Task Scheduler

URL: https://partyrock.aws/u/chnoel/mpBGSMr0O/SmartDay-AI-Task-Scheduler

## Project Overview

The AWS PartyRock Daily Task Scheduler is an AI-powered scheduling assistant that helps users organize daily tasks, evaluate workload feasibility, prioritize responsibilities, and create realistic schedules.

Built with AWS PartyRock, the application uses a multi-step AI workflow to turn user-provided tasks, deadlines, priorities, and scheduling preferences into an actionable daily plan.

## Features

- **Daily Schedule:** Generates a chronological, time-blocked schedule.
- **Priority Analysis:** Ranks tasks according to priority, deadlines, duration, dependencies when provided, and the selected scheduling strategy.
- **Feasibility Check:** Evaluates whether tasks can fit within the available time.
- **Productivity Recommendations:** Suggests practical adjustments to improve the daily plan.
- **End-of-Day Checklist:** Organizes planned work and identifies outstanding or deferred tasks.
- **Scheduling Constraints:** Accounts for fixed commitments, breaks, lunch windows, and optional buffer time.
- **Input Validation:** Identifies missing or invalid scheduling information.

## Technology Stack

| Technology | Purpose |
|---|---|
| AWS PartyRock | Application development and hosting environment |
| Amazon Bedrock-powered generative AI | AI capabilities provided through PartyRock |
| Prompt Engineering | Defines the behavior and constraints of each AI output |
| GitHub | Documentation and version control |
| Trello | Project planning and task management |

The application uses PartyRock's managed environment. It does not currently include a separately deployed backend or custom AWS infrastructure.

## Application Workflow

The application is organized as a PartyRock Flow with user input components and five AI-generated outputs.

### User Inputs

**Daily Tasks:** Tasks with names, priorities, estimated durations, deadlines, and dependencies where applicable.

**Day Start Time and Day End Time:** Defines the available scheduling window.

**Fixed Commitments:** Appointments or activities that must remain at specified times.

**Preferred Break Duration:** Specifies the duration of breaks.

**Break Frequency / Work Session Length:** Determines how often breaks should occur.

**Preferred Lunch Window:** Defines the preferred lunch period.

**Reserve Buffer Time:** Determines whether time should be reserved for transitions and unexpected delays.

**Scheduling Strategy:** Selects the approach used to organize tasks, such as Balanced Productivity.

**Additional Notes:** Provides extra preferences or scheduling constraints.

### AI Outputs

#### 1. Daily Schedule

Generates a time-blocked plan containing start times, end times, activities, durations, and brief explanations. Tasks that cannot fit are identified rather than silently omitted.

#### 2. Priority Analysis

Explains the order of tasks based on the selected strategy and the details supplied by the user. It focuses on task ranking and trade-offs rather than workload feasibility.

#### 3. Feasibility Check

Calculates whether the requested workload can fit within the available time after accounting for commitments, breaks, lunch, and buffer time.

The output reports one of three statuses:

- **Feasible:** The workload fits within the available time.
- **Feasible with Adjustments:** The workload may fit with reasonable changes.
- **Overloaded:** The requested workload exceeds the available capacity.

#### 4. Productivity Recommendations

Provides practical suggestions based on the schedule and workload analysis, including adjustments to task order, focus time, and deferred work.

#### 5. End-of-Day Checklist

Creates an actionable checklist to track planned activities, outstanding work, and deferred tasks.

## Design Principles

The application follows several important rules:

1. Respect the user's scheduling constraints.
2. Avoid overlapping activities and scheduling outside the available time window.
3. Use the selected scheduling strategy consistently.
4. Do not invent task names, durations, deadlines, or commitments.
5. Account for breaks, lunch, and buffer time when evaluating capacity.
6. Identify tasks that cannot fit within the available window.
7. Keep prioritization, feasibility analysis, scheduling, recommendations, and checklist generation focused on their separate responsibilities.
8. Maintain consistency across all five outputs.

## Setup and Usage

This application runs through AWS PartyRock and does not require local installation.

1. Open the shared PartyRock application.
2. Enter tasks, including priorities, durations, and deadlines where available.
3. Set the day's start and end times.
4. Provide fixed commitments, break preferences, lunch window, and buffer preference.
5. Select a scheduling strategy and enter any additional notes.
6. Generate and review all five outputs.
7. Adjust inputs and regenerate the outputs when necessary.

**PartyRock application URL:** Add your published or shared application link here.

## Repository Structure

```text
aws-partyrock-daily-task-scheduler/
├── README.md
├── TESTS.md
├── docs/
│   ├── application-workflow.md
│   └── prompt-design.md
├── screenshots/
│   ├── partyrock-flow.png
│   ├── daily-schedule.png
│   └── feasibility-check.png
└── .gitignore
```

## Limitations

- Results depend on the accuracy and completeness of user-provided information.
- AI-generated schedules and recommendations may require manual review.
- The current implementation runs within PartyRock's managed environment.
- Calendar integration, persistent task storage, automated reminders, and custom backend services are not currently implemented.

## Future Improvements

Potential extensions include calendar integration, recurring tasks, persistent preferences, automated rescheduling, notifications, and a custom web application backed by AWS services such as AWS Lambda, Amazon API Gateway, and Amazon DynamoDB.

## Learning Outcomes

This project provides experience with AI application development, prompt engineering, multi-step workflows, scheduling constraints, output validation, and software project management using GitHub and Trello.

## Project Status

**Status:** Functional prototype completed and tested.

The application includes five AI-generated outputs and has been tested using an intentionally overloaded daily schedule. Additional edge-case testing can further validate its reliability.
