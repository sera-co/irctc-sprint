Problem 1: Tatkal Booking Crashes at 10:00 AM

What is broken:
Tatkal booking flow becomes unusable at exactly 10:00 AM due to server overload. The system provides no feedback, queue, or recovery mechanism.

Affected users:
Urgent travelers, daily commuters, and users booking last-minute tickets (millions daily).

Frequency:
Occurs every day at 10:00 AM (Tatkal opening time).

Current flow — step by step:

User opens IRCTC at 9:50 AM
Logs into account
Searches train between two stations
Selects train and quota (Tatkal)
Waits on booking page until 10:00 AM
Clicks “Book Now” immediately at 10:00 AM
Page freezes / shows error / reloads
User retries multiple times
After 2–3 minutes, tickets show “Not Available”

Where exactly it breaks:
Step 6–7: When all users hit the booking endpoint simultaneously, the backend cannot handle concurrent requests → server crash / timeout.

Problem 2: Search Filters Do Not Work Reliably

What is broken:
Filters like class, availability, and departure time either don’t apply correctly or reset unexpectedly.

Affected users:
All users searching trains, especially new users and elderly users.

Frequency:
Very high — occurs in every search session.

Current flow — step by step:

User searches trains between two cities
Results list appears
User applies filter (e.g., Sleeper class)
Results update partially or incorrectly
User applies second filter (availability)
Results become inconsistent or unchanged
User clicks a train → navigates back
Filters reset automatically

Where exactly it breaks:
Step 4–6: Filter logic is inconsistent with backend data.
Step 8: UI state is not preserved → filters reset.

Problem 3: Seat Selection Resets

What is broken:
Selected seat preference (e.g., lower berth) is not retained in the next step.

Affected users:
Families, elderly passengers, and users with berth preference needs.

Frequency:
Medium to high — occurs frequently during booking.

Current flow — step by step:

User searches and selects train
Proceeds to passenger details page
Selects berth preference (e.g., Lower)
Clicks “Continue”
Moves to next page
Checks seat selection
Preference is missing or reset

Where exactly it breaks:
Step 4–5: Data is not persisted correctly between frontend and backend.

Problem 4: Payment Failure Without Recovery

How I found it:
While attempting a booking flow and reaching the payment page.

What is broken:
If payment fails, the booking session is lost and the user must restart the entire process.

Affected users:
All users making online payments, especially during peak times.

Frequency:
High — payment gateway failures are common.

Current flow — step by step:

User completes passenger details
Proceeds to payment page
Selects payment method (UPI/card)
Enters details
Payment fails due to timeout or gateway issue
User is redirected back
Booking session expires
User must restart entire process

Where exactly it breaks:
Step 5–7: No session persistence or retry mechanism after payment failure.

Problem 5: No Predictive Insight for Waitlist Tickets

How I found it:
While checking ticket availability for long-distance travel.

What is broken:
Users see waitlist numbers but have no idea whether tickets will confirm.

Affected users:
Long-distance travelers, planners, and families.

Frequency:
Very high — most bookings involve waitlisted tickets.

Current flow — step by step:

User searches train
Sees ticket status (e.g., WL 45)
No additional information provided
User manually guesses probability
Books ticket anyway or abandons
Checks status repeatedly later

Where exactly it breaks:
Step 2–3: System shows raw data but no actionable insight.

Problem 6: Poor Mobile Web Experience

How I found it:
Opened IRCTC on mobile browser.

What is broken:
UI is not optimized for mobile — buttons overlap, scrolling is inconsistent, and forms are hard to use.

Affected users:
Mobile users (majority of Indian users).

Frequency:
Very high — affects most mobile sessions.

Current flow — step by step:

User opens IRCTC on mobile browser
Homepage loads with dense layout
User tries to search trains
Form fields are cramped
User scrolls → layout shifts
Buttons overlap or become hard to tap
Navigation becomes frustrating

Where exactly it breaks:
Step 4–6: Poor responsive design implementation.