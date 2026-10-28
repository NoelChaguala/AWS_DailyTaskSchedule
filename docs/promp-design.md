Build an AI Daily Task Scheduler
Create an AI-powered Daily Task Scheduler that helps students and professionals turn their daily responsibilities into a realistic, prioritized, time-blocked schedule.

The application should function as a personal planning assistant. It should analyze tasks, deadlines, available time, fixed commitments, and scheduling preferences before generating a practical daily plan.

1. Interface and Design
Create a clean, modern, professional productivity dashboard with a simple and intuitive layout.

Organize the interface into two main sections:

Daily Planning: Inputs for tasks, availability, commitments, and scheduling preferences.
AI Planning Results: Generated schedule, priority analysis, feasibility assessment, productivity recommendations, and end-of-day checklist.
Use clear headings, readable text, consistent formatting, and logically grouped widgets. Make the application easy to use for both students and working professionals.

2. Input Widgets
Create input widgets for the following information.

A. Daily Tasks
Allow users to enter multiple tasks. Each task should include:

Task name
Task description
Priority: High, Medium, or Low
Deadline, if applicable
Estimated duration in minutes or hours
Dependencies on other tasks, if applicable
If the platform does not support structured, repeatable task-entry widgets, provide a multiline text input with clear instructions and a sample task format.

B. Daily Availability
Allow users to specify:

Start time of the day
End time of the day
Fixed commitments, including classes, meetings, appointments, and other unavailable periods
Fixed commitments should include their start and end times whenever possible.

C. Break and Lunch Preferences
Allow users to specify:

Preferred break duration
Preferred frequency of breaks or work-session length
Preferred lunch time or time window
Whether buffer time should be reserved for unexpected tasks
D. Scheduling Preferences
Allow users to select one of the following scheduling strategies:

Hardest Tasks First: Prioritize demanding or important work earlier in the day when practical.
Deadline-Driven: Give greater weight to approaching deadlines and the time remaining to complete tasks.
Balanced Productivity: Balance priorities, deadlines, demanding work, and breaks throughout the day.
E. Additional Notes
Provide a text input for additional instructions, preferences, constraints, or scheduling considerations not covered by the other fields.

3. AI-Generated Output Widgets
Create five distinct AI-generated output widgets. Each output should have a clearly defined purpose and use the relevant user inputs.

A. Daily Schedule
Generate a chronological, time-blocked schedule.

For each scheduled activity, display:

Start time
End time
Task or activity name
Estimated duration
A brief note when useful
Include fixed commitments, requested breaks, and lunch when applicable.

Use a consistent time format throughout the schedule. Ensure that activities do not overlap and that scheduled tasks remain within the available time window.

Include all requested tasks when feasible. If some tasks cannot fit, list them separately as unscheduled or deferred tasks rather than silently omitting them.

B. Priority Analysis
Explain why tasks are scheduled in their particular order.

Consider:

User-assigned priorities
Approaching deadlines
Estimated task durations
Dependencies between tasks
The selected scheduling strategy
Identify important trade-offs when competing tasks cannot all be prioritized simultaneously.

Never invent priorities, deadlines, or dependencies that the user has not provided.

C. Feasibility Check
Assess whether the requested workload can realistically fit within the available day.

Consider task durations, fixed commitments, breaks, lunch, and buffer time.

Report one of the following statuses:

Feasible: All requested tasks fit within the available time and scheduling constraints.
Feasible with Adjustments: The schedule requires an explicitly identified compromise or an optional preference to be relaxed.
Overloaded: The requested workload cannot fit within the available time under the stated constraints.
Explain the reasons for the assessment. When the workload is overloaded, estimate the time shortage when sufficient information is available and recommend which tasks to defer or reschedule.

Do not label a schedule feasible if it contains overlapping activities, violates fixed commitments, or exceeds the available time.

D. Productivity Recommendations
Provide practical recommendations based on the generated schedule.

Include relevant suggestions for:

Focused work sessions
Break timing and duration
Managing demanding tasks
Buffer time for unexpected work
Adjusting the workload when time is insufficient
Keep recommendations consistent with the actual schedule. Do not recommend activities that conflict with fixed commitments or scheduled tasks.

E. End-of-Day Checklist
Generate a checklist-style list of the tasks included in the planned schedule.

Use the same task names as the Daily Schedule. Include deferred tasks in a separate section when applicable.

Make it easy for users to review their responsibilities. Treat this as a planning checklist, not as persistent task-completion tracking.

4. Scheduling Rules and Constraints
Apply the following rules when generating all outputs.

Respect availability: Schedule activities only within the user's specified planning window.
Respect fixed commitments: Never schedule tasks or breaks over fixed commitments. If fixed commitments overlap, flag the conflict.
Use realistic durations: Allocate the estimated duration supplied for each task. Do not silently shorten tasks to make everything fit.
Respect deadlines: Consider approaching deadlines when prioritizing tasks, but never invent missing deadline information.
Apply the selected strategy: Adapt task ordering and explain important decisions based on the user's scheduling preference.
Include breaks and lunch: Schedule requested breaks and lunch when feasible. Do not treat unavailable periods as working time.
Account for buffer time: Reserve buffer time when possible and report when the available time does not permit it.
Respect dependencies: Schedule prerequisite tasks before dependent tasks whenever the constraints permit.
Prevent overlaps: No two scheduled activities may occupy the same time period.
Handle missing information: Request clarification or clearly state assumptions when essential information is missing. Never fabricate task details.
Handle overloaded days honestly: Identify tasks that cannot fit and recommend deferring or rescheduling them. Do not produce an impossible schedule as if it were valid.
Maintain output consistency: Ensure that the schedule, priority analysis, feasibility check, recommendations, and checklist agree on task names, times, and scheduling decisions.
Preserve user intent: Do not silently discard tasks or relax important constraints to create a more attractive-looking schedule.
5. Widget Connections and AI Behavior
Connect the input widgets to the appropriate AI-generated output widgets.

Task information must inform the Daily Schedule, Priority Analysis, Feasibility Check, and End-of-Day Checklist.
Availability and fixed commitments must inform the Daily Schedule and Feasibility Check.
Break and lunch preferences must inform the Daily Schedule and Productivity Recommendations.
Scheduling preferences must influence task ordering and the explanations provided by the Priority Analysis.
Additional notes must influence relevant scheduling decisions.
All outputs must use the same current set of user inputs.
When a user changes an input and regenerates the results, the affected outputs should reflect the updated information. Avoid contradictory recommendations, unrelated output, and unsupported assumptions.

6. Error Handling and Edge Cases
The application should handle the following situations clearly:

No tasks have been entered.
A task is missing its estimated duration.
The end time is earlier than or equal to the start time.
A task deadline falls outside the available planning window.
Fixed commitments overlap.
The total workload exceeds available time.
The user requests more breaks or buffer time than the day can accommodate.
Task dependencies make the requested schedule infeasible.
In these situations, explain the issue and request clarification or suggest adjustments instead of presenting unreliable results.

7. Scope and Platform Constraints
Build the initial version using AWS PartyRock's available application-generation and AI widget capabilities.

Prioritize the core scheduling experience over advanced features. Do not require a custom backend, external database, user authentication, persistent task history, or calendar integration.

If a requested interaction or feature is not supported by PartyRock's available widgets, use the simplest practical alternative and clearly communicate the limitation.

8. Initial Validation
After generating the application, verify that the input widgets and AI-generated outputs work together as intended.

Use a test scenario with eight hours of requested tasks and only four hours of available working time. Confirm that the Feasibility Check identifies the workload as overloaded, explains the time shortage, and recommends tasks to defer instead of creating an impossible schedule.

Also verify that multiline task entry works when repeatable task-entry widgets are unavailable, and that the generated outputs reflect changes to the user's inputs.

Final Objective
Deliver a functional AI Daily Task Scheduler prototype that accepts user-provided tasks and scheduling constraints, generates a realistic daily plan, explains its scheduling decisions, identifies infeasible workloads, and provides actionable productivity recommendations.

The application should prioritize accuracy, usability, transparency, and consistency over generating a complete-looking schedule at all costs.