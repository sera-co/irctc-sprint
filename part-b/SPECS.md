Feature Spec 1: Tatkal Virtual Queue System
Problem Statement

From Part A Problem 1, Tatkal booking crashes at 10:00 AM due to massive simultaneous requests. Users get no feedback and lose tickets unfairly.

Current State (from Part A)

Users log in → search → click book at 10:00 AM → system freezes/crashes → retry → tickets gone.

Proposed Solution

Introduce a Virtual Queue System where users are placed in a queue before booking instead of hitting servers simultaneously.

Proposed User Flow — Step by Step
User clicks “Book Tatkal”
System assigns queue position
User sees wait time + progress bar
When turn arrives → auto redirect
User gets 2-minute booking window
Technical Implementation Plan

System components affected:

Booking service
Load balancer
Session manager

New data requirements:

Queue ID
Position
Timestamp

API changes:

/queue/join
/queue/status

Frontend changes:

Queue UI screen
Real-time updates

Third-party services:

Redis for queue handling
Success Metrics
Booking success rate ↑
Server crashes ↓
User retries ↓
Edge Cases and Constraints
Refresh → maintain queue
Timeout → next user
API delay fallback
Wireframe
7
Feature Spec 2: Persistent Smart Filters
Problem Statement

From Problem 2, filters don’t work reliably and reset, causing confusion.

Current State

Filters behave inconsistently and disappear after navigation.

Proposed Solution

Add Persistent Smart Filters with real-time results.

Proposed User Flow
User searches trains
Applies filters
Results update instantly
Navigates back → filters remain
Technical Implementation

Components:

Search API
Frontend state manager

Data:

Filter state storage

API:

/search?filters=

Frontend:

Filter chips
Sticky filter bar
Success Metrics
Faster booking decisions
Reduced confusion
Edge Cases
No results → suggestions
Wireframe
6
Feature Spec 3: Seat Preference Persistence
Problem Statement

From Problem 3, seat selection resets after proceeding.

Current State

User selects preference → system loses it.

Proposed Solution

Ensure seat preference persistence across steps.

Proposed User Flow
User selects berth
Clicks continue
Preference saved and shown next screen
Technical Implementation

Components:

Booking flow
Passenger API

Data:

Seat preference field

Frontend:

State persistence
Success Metrics
Reduced frustration
Better booking accuracy
Edge Cases
Seat unavailable → fallback message
Feature Spec 4: Payment Retry & Resume
Problem Statement

From Problem 4, failed payments reset booking.

Current State

Payment fails → user restarts.

Proposed Solution

Retry Payment + Auto Resume Booking

Proposed User Flow
Payment fails
User sees retry option
Session preserved
Retry payment
Technical Implementation

Components:

Payment gateway
Session manager

Data:

Booking session ID

API:

/payment/retry
Success Metrics
Payment success ↑
Drop-offs ↓
Feature Spec 5: Waitlist Prediction Indicator
Problem Statement

From Problem 5, no clarity on waitlist confirmation.

Current State

User sees WL number only.

Proposed Solution

Show prediction probability (e.g., 80% chance).

Proposed User Flow
User searches train
Sees WL + prediction
Makes informed decision
Technical Implementation

Components:

Prediction engine

Data:

Historical booking data
Success Metrics
Better decision making
Reduced cancellations
Feature Spec 6: Mobile-Optimized UI
Problem Statement

From Problem 6, mobile UI is broken and hard to use.

Current State

Poor responsiveness, overlapping elements.

Proposed Solution

Responsive mobile-first redesign

Proposed User Flow
User opens mobile site
Clean layout loads
Easy navigation and booking
Technical Implementation

Components:

Frontend redesign

Frontend:

Responsive layout
Touch-friendly UI
Success Metrics
Mobile conversion ↑
Bounce rate ↓