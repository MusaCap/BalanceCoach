# Data Model: Energy & Spending Balance Coach

This document defines the full data model for the Energy & Spending Balance Coach application, including
entities, relationships, and field-level definitions for all major data structures.

The model is platform-agnostic (works for SQL, NoSQL, ORM, Firebase, etc.).

---

# 1. Entity Relationship Overview

**Core Domains**
1. User Profile  
2. Biometric Data  
3. Mood Tracking  
4. Financial Data  
5. Insights & Scoring  
6. Coaching & Recommendations  
7. Historical Aggregates  

These domains interact through the `User` entity as the central anchor.

---

# 2. Entities & Schemas

## 2.1 User

Represents the primary user and all profile-level settings.

### Table: `users`

| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | Primary key |
| `email` | string | Login identifier |
| `password_hash` | string | Hashed password (if not OAuth) |
| `name` | string | Display name |
| `timezone` | string | Used for daily calculations (e.g., "America/Los_Angeles") |
| `currency` | string | Default currency (USD, GBP, etc.) |
| `created_at` | datetime | Account creation |
| `updated_at` | datetime | Last change |

### Table: `user_settings`

| Field | Type | Description |
|--------|------|-------------|
| `user_id` | UUID | FK → users.id |
| `goals` | json | Array of goals: ["reduce_impulse_spending", "increase_energy"] |
| `notification_preferences` | json | Delivery rules |
| `biometric_integrations` | json | List of connected wearables |
| `financial_integrations` | json | Connected banks, cards |
| `mood_reminder_time` | time | Daily check-in reminder |

---

## 2.2 Biometric Data

Incoming signals from wearables and health APIs.

### Table: `biometric_readings`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `user_id` | UUID | FK |
| `source` | string | e.g., "oura", "fitbit", "apple_health" |
| `timestamp` | datetime | When reading was taken |
| `sleep_score` | int | Composite sleep score (0–100) |
| `sleep_duration_minutes` | int | Total minutes asleep |
| `resting_heart_rate` | int | BPM |
| `hrv` | int | HRV metric (ms) |
| `steps` | int | Steps taken that day |
| `activity_calories` | int | Calorie expenditure |
| `stress_level` | int | Normalized 0–100 |
| `raw_payload` | json | Original input for debugging |

**Indexes:** `(user_id, timestamp)`

---

## 2.3 Mood Tracking

Subjective emotional state + optional triggers.

### Table: `mood_entries`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `user_id` | UUID | FK |
| `timestamp` | datetime | Mood check time |
| `mood_score` | int | Range: -5 to +5 or 1–7 depending on UI |
| `emotion_tags` | json | e.g., ["stressed", "bored", "happy"] |
| `notes` | text | Optional free-text |
| `energy_level_self_reported` | int | 0–100 |
| `context_tags` | json | e.g. ["work", "social", "home"] |

---

## 2.4 Financial Data

Transactions, merchants, budgets, and categories.

### Table: `accounts`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `user_id` | UUID | FK |
| `provider` | string | "plaid", "stripe", etc. |
| `external_account_id` | string | Provider account ID |
| `account_name` | string | e.g., "Checking", "Amex Gold" |
| `account_type` | string | "checking", "credit_card", "investment" |
| `created_at` | datetime | Integration time |

### Table: `transactions`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `user_id` | UUID | FK |
| `account_id` | UUID | FK |
| `timestamp` | datetime | Transaction date |
| `merchant_name` | string | Cleaned merchant name |
| `amount` | decimal | Positive = spend, negative = income |
| `category` | string | Auto or manually assigned category |
| `subcategory` | string | Fine-grained categorization |
| `is_discretionary` | boolean | Derived by ML model |
| `is_recurring` | boolean | ML-detected subscription |
| `notes` | text | User notes |
| `raw_payload` | json | Original provider response |

**Indexes:** `(user_id, timestamp)` and `(user_id, category)`

---

## 2.5 Insights & Scores

The intelligence layer that sits on top of biometrics, mood, and spending.

### 2.5.1 Daily Balance Score

Represents the combined view of energy, stress, mood, and financial behavior.

### Table: `daily_balance_scores`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `user_id` | UUID | FK |
| `date` | date | Day of score |
| `energy_score` | int | Derived from biometrics (0–100) |
| `mood_score` | int | Derived from mood entries (0–100) |
| `financial_score` | int | Derived from spending behavior (0–100) |
| `composite_score` | int | Weighted formula |
| `insights_generated` | boolean | Whether insights were created for coach |

---

### 2.5.2 Correlation Insights

Stores detected relationships (e.g., low sleep → increased spending).

### Table: `correlation_insights`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | PK |
| `user_id` | UUID | FK |
| `detected_at` | datetime | Timestamp of computation |
| `signal_type` | string | e.g., "sleep_to_spending", "mood_to_impulse" |
| `correlation_strength` | float | -1 to +1 |
| `description` | text | Human readable summary |
| `supporting_data` | json | Statistical details |

---

## 2.6 Coaching System

### 2.6.1 Recommendations

Generated coaching messages tied to user state.

### Table: `recommendations`

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | PK |
| `user_id` | UUID | FK |
| `timestamp` | datetime | When recommendation created |
| `type` | string | "financial", "energy", "mood", "combined" |
| `message` | text | Full recommendation text |
| `risk_level` | string | "low", "medium", "high" |
| `trigger_source` | string | e.g., "low_sleep", "high_stress", "spending_spike" |
| `metadata` | json | Additional model metadata |
| `user_feedback` | string | "helpful", "not_helpful", null |

---

## 2.7 Historical / Aggregate Tables

### Table: `weekly_summary`

| Field | Type | Description |
|--------|------|-------------|
| `user_id` | UUID | FK |
| `week_start_date` | date | Monday of week |
| `avg_energy_score` | int | |
| `avg_financial_score` | int | |
| `avg_mood_score` | int | |
| `total_spending` | decimal | |
| `discretionary_spending` | decimal | |
| `insights` | json | Summary insights |

### Table: `monthly_summary`

Same as weekly summary, but aggregated monthly.

---

# 3. Relationships

- **User 1:N BiometricReadings**
- **User 1:N MoodEntries**
- **User 1:N Accounts**
- **Account 1:N Transactions**
- **User 1:N DailyBalanceScores**
- **User 1:N CorrelationInsights**
- **User 1:N Recommendations**
- **User 1:N Weekly/Monthly summaries**

---

# 4. Derived Fields & ML Features

These values are not stored directly but computed when needed.

### Behavioral Features
- `avg_spend_last_7_days`
- `discretionary_spend_ratio`
- `impulse_spend_flag`
- `recurring_payment_probability`

### Biometric Features
- `sleep_deficit = sleep_duration - ideal_sleep`
- `hrv_z_score`
- `stress_trend_7_days`

### Mood Features
- `mood_volatility`
- `mood_spend_correlation`
- `energy_mood_correlation`

---

# 5. Event Log Model (Optional)

### Table: `event_log`

Captures all behavioral and system events (useful for RL/AI).

| Field | Type | Description |
|--------|------|-------------|
| `id` | UUID | PK |
| `user_id` | UUID | FK |
| `event_type` | string | e.g., "recommendation_viewed", "transaction_added" |
| `metadata` | json | Additional context |
| `timestamp` | datetime | |

---

# 6. Data Retention & Cleanup Policies

- Raw biometric & financial payloads retained 30–90 days for debugging.
- Aggregates (daily/weekly/monthly) retained indefinitely.
- Users can purge all mood entries, biometrics, transactions, or insights.

---

# 7. Future Model Extensions

- Social/cohort benchmarking tables
- Predictive spend category forecasting tables
- Burnout risk classification model outputs
- Fine-grained anomaly detection tables per signal

