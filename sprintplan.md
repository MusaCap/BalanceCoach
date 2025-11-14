# Sprint Plan: Energy & Spending Balance Coach
This sprint plan is optimized for **Windsurf’s single-window agentic workflow**, enabling continuous development, testing, refactoring, and iteration inside one AI-driven IDE instance.

The plan assumes:
- 6–8 week build (MVP)
- 2-week sprints
- A cross-functional team using Windsurf (PM, engineering, AI engineer, data engineer)
- Continuous integration via Windsurf agent chains
- Code-first execution with rapid prototyping

---

# Sprint 0 – Foundations (1 week)

## Objectives
- Establish repo, architecture, and core scaffolding.
- Define data schema, environment variables, and integration stubs.
- Configure Windsurf agents for development automation.

## Tasks
- [ ] Initialize monorepo (`frontend/`, `backend/`, `infra/`)
- [ ] Configure environment setup (`.env.example`, secrets layout)
- [ ] Set up WindSurf pipelines:
  - Code generation agent
  - Test writing agent
  - Document agent
- [ ] Generate base data model from PRD (auto-insert SQL/NoSQL scaffolding)
- [ ] Implement backend boilerplate:
  - Auth scaffolding
  - User table
  - Settings table
- [ ] Install API SDK wrappers (Plaid, Apple Health/Oura placeholder modules)
- [ ] Implement error logging & observability hooks
- [ ] Generate initial OpenAPI spec template

## Deliverables
- Repo scaffolding
- Base schema migration
- WindSurf agent config
- Initial API spec
- CI tests for health check

---

# Sprint 1 – Onboarding & Accounts (2 weeks)

## Objectives
- Create full onboarding experience.
- Implement authentication, profile setup, and permission flows.
- Create data ingestion placeholders for biometrics and transactions.

## Backend Tasks
- [ ] Implement Sign Up / Login / OAuth
- [ ] Create endpoints for:
  - Profile settings
  - Notification preferences
  - Integrations list
- [ ] Add wearable integration placeholder endpoints
- [ ] Add bank integration placeholder endpoints
- [ ] Implement Jobs for async data pull (cron or queue)

## Frontend Tasks
- [ ] Build onboarding UI
  - Email/OAuth sign-in
  - Profile setup page
  - Goals selection UI
- [ ] Build integration connection screens
- [ ] Build initial navigation framework

## WindSurf Workflow
- Use "Orchestrate" agent to generate React UI from Figma-like instructions.
- Use "Refactor" agent for backend modularization.
- Use "Test" agent to auto-generate Jest/Pytest suites.

## Deliverables
- Fully functional onboarding
- Multi-platform login
- User settings management
- Integration connection UX
- Initial styling/theme

---

# Sprint 2 – Financial Data Pipeline (2 weeks)

## Objectives
- Implement bank connection flow.
- Ingest and store transactions.
- Run daily sync jobs.
- Build category + discretionary/income logic.

## Backend Tasks
- [ ] Implement Plaid OAuth/token exchange
- [ ] Implement `/transactions/sync` endpoint
- [ ] Build transaction parser & classifier
- [ ] Implement category mapping rules
- [ ] Add ML model placeholder for discretionary spending detection
- [ ] Add recurring payment detector

## Frontend Tasks
- [ ] Spending overview UI
- [ ] Transaction list + details screen
- [ ] Category editing UI
- [ ] Loading & batch sync indicators

## Windsurf Workflow
- Use Windsurf to generate:
  - Transaction import pipeline
  - Category ML stub
  - Full table migrations
- Use Windsurf Agents to batch-generate test data.

## Deliverables
- End-to-end transaction ingestion
- Daily sync job
- Editable categories UI
- Basic financial insights visible

---

# Sprint 3 – Biometric + Mood Pipeline (2 weeks)

## Objectives
- Fully implement biometric ingestion.
- Implement mood logging system.
- Map biometrics → energy state.

## Backend Tasks
- [ ] Implement ingest endpoints for:
  - Sleep
  - HRV
  - RHR
  - Steps
- [ ] Build cron to ingest biometrics nightly
- [ ] Normalize values to user baseline
- [ ] Implement /mood/new endpoint
- [ ] Derive `energy_score` from biometrics

## Frontend Tasks
- [ ] Mood slider UI
- [ ] Emotion tags selector
- [ ] Mood history view
- [ ] Daily biometrics dashboard

## Windsurf Workflow
- Use Model Builder agent to generate:
  - Biometric → energy scoring function
  - Sleep deficit normalization
- Use Unit Test agent to write tests for mood & biometrics.

## Deliverables
- Full biometric ingestion pipeline
- Mood logging flow
- Energy score calculations
- UI for biometrics & mood review

---

# Sprint 4 – Balance Score & Insight Engine (2 weeks)

## Objectives
- Implement daily composite scoring.
- Build insight engine: correlations, predictions, trends.
- Start generating basic recommendations.

## Backend Tasks
- [ ] Build `/scores/daily` generator
- [ ] Create insight engine modules:
  - Correlation detection (sleep → spend)
  - Trend analysis (mood → discretionary spending)
  - Biomarker anomaly detector
- [ ] Build prediction module (risk scoring)
- [ ] Implement recommendations table

## Frontend Tasks
- [ ] Build Daily Balance Score UI
- [ ] Score breakdown modal
- [ ] Insight feed UI
- [ ] Weekly/Monthly score views

## Windsurf Workflow
- Use "Insight Generator" agent:
  - Multivariate correlation code generation
  - Time-series inference logic
- Use Windsurf’s natural language-to-code refinements to iterate recommendations.

## Deliverables
- Fully functioning daily balance score
- Automated correlations
- Insight feed populated
- UX for insights and scores

---

# Sprint 5 – Coaching Engine & Alerts (2 weeks)

## Objectives
- Build the coaching system end-to-end.
- Implement contextual nudges and real-time alerts.
- Add recommendation feedback loop.

## Backend Tasks
- [ ] Create rule-based + ML hybrid recommendation generator
- [ ] Implement push notification service
- [ ] Add impulse risk scoring
- [ ] Add burnout prediction scoring
- [ ] Build feedback endpoint for "helpful/not helpful"

## Frontend Tasks
- [ ] Coaching feed experience
- [ ] Alert notification UI
- [ ] Feedback buttons on recommendations

## Windsurf Workflow
- Use Recommendation Agent to:
  - Auto-generate recommendation templates
  - Improve natural language phrasing
  - Test outputs against sample inputs
- Use Windsurf to simulate high-risk days with synthetic data.

## Deliverables
- Real-time coaching alerts
- Smart recommendations
- Risk-based nudges
- User feedback loop integrated

---

# Sprint 6 – Dashboards, Polish, and MVP Launch (1–2 weeks)

## Objectives
- Build final dashboards.
- Improve speed, caching, stability.
- QA & refine all UX flows.

## Backend Tasks
- [ ] Implement caching on heavy queries
- [ ] Tune cron jobs for sync reliability
- [ ] Harden error handling
- [ ] Finalize data retention rules

## Frontend Tasks
- [ ] Build unified dashboard
- [ ] Add trend visualizations (charts)
- [ ] Polish mobile experience
- [ ] Add loading/skeleton animations

## Windsurf Workflow
- Use Refactor Agents to unify code style.
- Use Visual Agent to generate chart components.
- Use Testing Agent to run final regression suite.

## Deliverables
- Polished MVP
- Charts + insights + score dashboard
- Fully integrated coaching engine
- Ready for first user cohort

---

# Summary Timeline

| Sprint | Duration | Focus Area |
|--------|----------|-------------|
| Sprint 0 | 1 week | Foundations, repo, schema |
| Sprint 1 | 2 weeks | Onboarding & integrations |
| Sprint 2 | 2 weeks | Financial pipeline |
| Sprint 3 | 2 weeks | Biometric & mood ingestion |
| Sprint 4 | 2 weeks | Insights & scoring |
| Sprint 5 | 2 weeks | Coaching system & alerts |
| Sprint 6 | 1–2 weeks | Dashboards & polish |

Total: **10–13 weeks** depending on team size and complexity.

---

# Windsurf-Specific Execution Strategy

1. **Single Window Mode**:  
   Use the central coding window with multi-agent flows for:
   - Code generation
   - Testing
   - Refactoring
   - Documentation generation

2. **Agent Chain Setup**:
   - "Architect" → generate structure
   - "Engineer" → build modules
   - "Refactor" → consolidate logic
   - "Tester" → write/execute tests
   - "Documenter" → auto-update README/API docs

3. **Sprint-by-Sprint Scaffolding**:
   At the start of each sprint:
   - Paste sprint goals into Windsurf.
   - Generate file scaffolds.
   - Let Windsurf auto-create stubs, interfaces, schema migrations.

4. **Continuous Testing**:
   - Use the Test Agent to automatically generate test suites per module.

5. **Continuous Refactoring**:
   - Trigger Windsurf’s refactor agent at each milestone for consistency.

---

# Final Output
A fully functional, AI-powered energy + spending wellness app with:
- Biometric ingestion
- Financial ingestion
- Mood tracking
- Daily balance score
- Insight engine
- Recommendation engine
- Fully polished dashboard

Designed and executed entirely through **Windsurf in a single development window**.

