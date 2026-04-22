AI Feature Specification: Waitlist Prediction Engine
Problem It Solves

Addresses Problem 5 (No Predictive Insight).

Proposed Feature — User Perspective

User sees:
“WL 45 → 82% chance of confirmation”

Model or API Choice
Gradient Boosting / XGBoost (best for tabular prediction)
Training Data
Historical booking data
Cancellation trends
Seasonal patterns
How Output Is Shown

Inline in search results beside train:

WL 45 | 🔮 82% Confirm

Confidence Threshold and Fallback
Show only if confidence > 70%
Else: “Prediction unavailable”
Success Metrics
Increased bookings
Reduced cancellations
Limitations and Risks
Prediction errors
Seasonal bias
📄 part-b/MATRIX.md
Impact vs Effort Matrix
The Matrix
	Low Effort	High Effort
High Impact	Smart Filters, Payment Retry	Tatkal Queue, Waitlist AI
Low Impact	Seat Persistence	Mobile Redesign
Placement Justifications
Tatkal Queue — High Impact / High Effort

Affects millions daily (high impact). Requires backend queue system (high effort). Must be prioritized despite complexity.

Smart Filters — High Impact / Low Effort

Used in every search (high impact). Mostly frontend + API tweaks (low effort). Quick win.

Seat Persistence — Low Impact / Low Effort

Affects fewer users but easy fix. Good polish feature.

Payment Retry — High Impact / Low Effort

Reduces drop-offs. Simple session handling improvement.

Waitlist AI — High Impact / High Effort

Requires ML + data pipeline. Valuable but complex.

Mobile UI — Low Impact / High Effort

Large effort redesign but not core failure.

Recommended Sprint Order
Smart Filters
Payment Retry
Tatkal Queue
Seat Persistence
Waitlist AI
Mobile Redesign