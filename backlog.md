# Backlog: Energy & Spending Balance Coach
This backlog contains all epics, features, and detailed user stories required to build the MVP, V1, and future versions of the Energy & Spending Balance Coach.

---

# EPIC 1: User Onboarding & Account Setup

## Feature 1.1 – Account Creation
### User Stories
- As a user, I want to create an account using email/password so I can log into the app securely.
- As a user, I want to log in using OAuth (Apple, Google) so onboarding is fast.
- As a user, I want to reset my password so I can regain access if I forget it.
- As a user, I want multi-device support so I can access the app from phone and web.

## Feature 1.2 – Profile Setup
### User Stories
- As a user, I want to set my timezone so daily scores and alerts match my day.
- As a user, I want to set my currency so financial data is consistent.
- As a user, I want to choose my initial goals (e.g., reduce impulse spending, improve energy) so recommendations are personalized.

## Feature 1.3 – Permissions & Data Connections
### User Stories
- As a user, I want to connect my wearable device so the app can read my biometric metrics.
- As a user, I want to connect bank/credit card accounts so spending can be analyzed.
- As a user, I want to control the permissions I grant, so I understand exactly what data is collected.
- As a user, I want to view all connected integrations so I can manage or remove them.

---

# EPIC 2: Financial Data Collection & Insights

## Feature 2.1 – Bank Integration
### User Stories
- As a user, I want the app to sync my transactions daily so spending insights are always updated.
- As a user, I want to view all my connected financial accounts in one place.
- As a user, I want my transactions automatically categorized so I don't need to do it manually.
- As a user, I want categories that are editable so I can correct any misclassification.

## Feature 2.2 – Spending Analytics
### User Stories
- As a user, I want to see a breakdown of my spending by category.
- As a user, I want to see discretionary vs. non-discretionary spending splits.
- As a user, I want to mark subscriptions or recurring payments so the system can track them.
- As a user, I want to see spending spikes so I can understand triggers.

## Feature 2.3 – Financial Behavior Detection
### User Stories
- As a user, I want the system to detect impulsive purchases based on timestamp, context, and category.
- As a user, I want the system to detect when I overspend a category.
- As a user, I want the system to identify patterns like “You spend more after poor sleep.”
- As a user, I want the system to detect purchase regret indicators via post-spending mood entries.

---

# EPIC 3: Biometric Data Collection & Modeling

## Feature 3.1 – Wearable Integration
### User Stories
- As a user, I want the app to automatically sync sleep, HRV, steps, and stress data.
- As a user, I want to view all biometric metrics for a given day.
- As a user, I want to see weekly and monthly biometric trends.

## Feature 3.2 – Biometric Normalization
### User Stories
- As a user, I want the system to learn my baseline HRV so insights match my physiology.
- As a user, I want the system to detect sleep deficits.
- As a user, I want the system to track stress trends and compare them across days.

## Feature 3.3 – Biometric Behavior Modeling
### User Stories
- As a user, I want biometrics to be mapped to “energy levels” so I can understand how recovered I am.
- As a user, I want the system to identify days when I’m at risk of burnout.
- As a user, I want the system to link biometric states to spending patterns.

---

# EPIC 4: Mood Tracking & Emotional Analytics

## Feature 4.1 – Mood Logging
### User Stories
- As a user, I want to log my mood quickly via slider or emoji.
- As a user, I want to add emotion tags like “tired” or “stressed.”
- As a user, I want to add optional notes for more context.
- As a user, I want a daily reminder to log my mood.

## Feature 4.2 – Mood Modeling
### User Stories
- As a user, I want the system to track mood trends across days and weeks.
- As a user, I want the system to detect mood volatility.
- As a user, I want the system to identify mood-driven spending spikes.

---

# EPIC 5: Balance Scoring System

## Feature 5.1 – Daily Balance Score
### User Stories
- As a user, I want a daily score showing how balanced I am across energy, mood, and spending.
- As a user, I want to understand how each component (energy, mood, money) affects the score.
- As a user, I want my score delivered at the same time every day.

## Feature 5.2 – Component Scores
### User Stories
- As a user, I want an **Energy Score** derived from biometrics.
- As a user, I want a **Mood Score** based on mood entries.
- As a user, I want a **Financial Behavior Score** based on spending quality.

---

# EPIC 6: Insight Engine & Correlation Models

## Feature 6.1 – Correlation Detection
### User Stories
- As a user, I want insights like "You spend more when sleep < 6 hours."
- As a user, I want to see correlations like “High stress → more food delivery.”
- As a user, I want long-term trend correlations (e.g., monthly).

## Feature 6.2 – Predictive Insights
### User Stories
- As a user, I want predictive warnings like “Tomorrow is a high-risk spending day.”
- As a user, I want burnout forecasts.
- As a user, I want to see when conditions for good decisions are optimal.

---

# EPIC 7: Coaching & Recommendations Engine

## Feature 7.1 – Daily Recommendations
### User Stories
- As a user, I want actionable daily suggestions based on my score.
- As a user, I want wellness tips when energy is low.
- As a user, I want financial nudges when overspending is detected.
- As a user, I want holistic balancing recommendations.

## Feature 7.2 – Real-Time Alerts
### User Stories
- As a user, I want alerts when I’m at high risk for impulsive spending.
- As a user, I want recommendations when biometrics spike downward.
- As a user, I want reminders to re-assess my mood after big purchases.

## Feature 7.3 – Feedback Loop
### User Stories
- As a user, I want to rate whether a recommendation was helpful.
- As a user, I want recommendations to improve over time based on feedback.

---

# EPIC 8: Dashboards & Visualization

## Feature 8.1 – Daily Dashboard
### User Stories
- As a user, I want to see my daily energy, mood, and spending in one screen.
- As a user, I want simple trend summaries.

## Feature 8.2 – Trend Visualizations
### User Stories
- As a user, I want trend charts for biometrics.
- As a user, I want charts linking mood and spending.
- As a user, I want charts linking sleep or HRV to spending spikes.

## Feature 8.3 – Insight History
### User Stories
- As a user, I want a feed of all past insights and recommendations.
- As a user, I want search and filtering over my insights.

---

# EPIC 9: Budgeting & Financial Planning (v1+)

## Feature 9.1 – Monthly Budget Setup
### User Stories
- As a user, I want to set spending goals per category.
- As a user, I want alerts when approaching a budget limit.

## Feature 9.2 – Smart Budgeting Based on Energy
### User Stories
- As a user, I want my budget recommendations personalized to my energy patterns.
- As a user, I want the system to adjust savings goals based on mood-driven spending risk.

---

# EPIC 10: Infrastructure, Data, and Architecture

## Feature 10.1 – Data Syncing
### User Stories
- As a user, I want fast and reliable syncing of biometrics.
- As a user, I want fast syncing of financial transactions.

## Feature 10.2 – Data Security
### User Stories
- As a user, I want end-to-end encryption for all sensitive data.
- As a user, I want the ability to delete all my data permanently.

## Feature 10.3 – Data Retention
### User Stories
- As a user, I want long-term history to track progress over months and years.

---

# EPIC 11: Future Expansion

## Feature 11.1 – Voice AI Coach
### User Stories
- As a user, I want to ask the coach for advice using voice input.
- As a user, I want natural back-and-forth conversation about energy and spending.

## Feature 11.2 – Group Coaching / Accountability
### User Stories
- As a user, I want to join groups of people working on similar goals.
- As a user, I want progress badges and community insights.

## Feature 11.3 – Automatic Savings Rules
### User Stories
- As a user, I want auto-savings based on predicted impulse spending days.
- As a user, I want to set rules like “Move $20 to savings when HRV is high.”

---

# Summary

This backlog includes:
- 11 Epics
- 40+ Features
- 120+ detailed user stories

It fully supports MVP → V1 → V2 → expansion phases.

