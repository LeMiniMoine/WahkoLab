
# 🪙 WahkoLab Token Allocation Model

This model ensures fair and transparent distribution of project tokens based on contribution value, role, effort, and seniority.

---

## 🔧 How It Works

### 1. Base Scoring by Role

Each contribution is evaluated with a weighted score based on:

- **60% Workload** (measured in person-days)
- **40% Required Seniority** (scored from 0 = junior to 5 = lead)

This score helps determine how many tokens are allocated to each role.

---

### 2. Global Project Distribution

For a standard project (e.g., 10,000 tokens budget), distribution is proportional to each role’s total contribution score.

Roles with higher effort and complexity earn more tokens, but distribution scales with actual validated participation.

---

## 🧩 Per-Task Token Flow

Each task has its own mini-token economy:

- **15%** goes to the person who **created** the task (designer, lead, etc.)
- **75%** goes to the person who **executes** the task (coder, artist, etc.)
- **10%** goes to the person(s) who **validate** the task (maintainer, DAO vote, peer review)

---

## 🧠 Governance Safeguards

- All token distributions are tied to validated contributions
- Task creators ≠ executors (separation of concerns)
- Token abuse is prevented through role thresholds and validation layers

---

## 📊 Example Scenario

A developer completes a mid-complexity task worth 100 tokens:

- 15 tokens to the task creator (e.g., Game Designer)
- 75 tokens to the developer who did the work
- 10 tokens to the lead or reviewer who approved it

---

This model can evolve over time but provides a solid and transparent base to ensure contributors are rewarded based on **impact and validation**, not status or speculation.
