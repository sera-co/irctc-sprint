Impact vs Effort Matrix
The Matrix
	Low Effort	High Effort
High Impact	Smart Filters, Payment Retry & Resume	Tatkal Virtual Queue, Waitlist Prediction (AI)
Low Impact	Seat Preference Persistence	Mobile UI Redesign
How I Scored Each Dimension
Impact Scoring (1–5)

I scored Impact based on:

Number of users affected (based on Part A frequency)
Whether the issue occurs in the core booking flow
Severity of failure (booking failure vs inconvenience)

👉 Example:

Tatkal crash = 5 (blocks booking completely)
Seat preference reset = 2 (inconvenience, not blocker)
Effort Scoring (1–5)

I scored Effort based on:

Number of system components affected
Backend vs frontend complexity
Need for new infrastructure (queue system, ML models)
Risk of breaking existing IRCTC flows

👉 Example:

Smart filters = 2 (frontend + minor API fixes)
Tatkal queue = 5 (backend architecture change)
Placement Justifications
Tatkal Virtual Queue — High Impact / High Effort

Impact is extremely high because this affects millions of users daily at 10:00 AM, completely blocking bookings.
Effort is high since it requires new backend queue infrastructure, session handling, and load balancing changes.
This belongs in this quadrant because it is critical but requires careful phased implementation.

Smart Filters — High Impact / Low Effort

Impact is high because every user interacts with search filters, and poor filtering directly slows down bookings.
Effort is low as it mainly involves frontend state management and improving API query handling.
This is a quick win and should be prioritized early in the sprint.

Payment Retry & Resume — High Impact / Low Effort

Impact is high since payment failures lead to complete booking loss, directly affecting revenue and user trust.
Effort is relatively low because it involves session persistence and retry logic, not a full system redesign.
This makes it another top-priority feature for immediate implementation.

Seat Preference Persistence — Low Impact / Low Effort

Impact is lower since it does not block booking but affects user comfort and satisfaction.
Effort is low as it requires fixing state persistence between steps.
This is a good polish feature after critical fixes.

Waitlist Prediction (AI) — High Impact / High Effort

Impact is high because it helps users make better booking decisions, especially for long-distance travel.
Effort is high due to data collection, model training, and integration into the system.
This should be planned as a mid-to-long term feature, not immediate sprint work.

Mobile UI Redesign — Low Impact / High Effort

Impact is moderate but not critical to booking success (users can still complete flows).
Effort is high because it requires a complete responsive redesign across multiple screens.
This is best handled as a separate design initiative, not part of the core sprint.

Recommended Sprint Order
Smart Filters — fastest improvement with high visibility
Payment Retry & Resume — prevents booking loss
Tatkal Virtual Queue — critical but complex (start early, release carefully)
Seat Preference Persistence — quick UX win
Waitlist Prediction (AI) — build after data readiness
Mobile UI Redesign — long-term redesign effort