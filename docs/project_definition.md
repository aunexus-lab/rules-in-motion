# System Map + Workflow Automation Prototype 

(Systems Thinking + Computational Logic + HCI)

### Project overview

Many operational failures come from unclear workflow rules, hidden assumptions, and poor handoffs.

This project asks students to build a GitHub repo that:

- models a real workflow as a **system**
- defines a **rules specification** with edge cases
- implements a small prototype (CLI / web / API)
- includes tests and documentation so the workflow can be reviewed and improved

### Nexus alignment

- **Primary domains:** Systems Thinking, Computational Logic, Human-Computer Interaction
- **Secondary domains:** Adaptive Infrastructure, Cognitive Architecture

### Student-facing learning outcomes

By the end, students should be able to:

- define system boundaries, actors, states, and dependencies
- translate workflow rules into a clear, testable specification
- implement rule logic and handle edge cases
- design an interaction that communicates status and uncertainty clearly
- ship a repo that another student can run and evaluate

---

### Workflow options (choose one)

Pick one workflow that is common and has clear failure modes.

1. **Student onboarding workflow**
    - Inputs: student profile + required steps
    - Output: next-step recommendations + completion status
2. **Helpdesk triage workflow**
    - Inputs: ticket text + category + urgency signals
    - Output: routing decision + SLA target + escalation rules
3. **Appointment scheduling workflow**
    - Inputs: availability, constraints, priorities
    - Output: proposed schedule + conflict explanations
4. **Course project intake workflow**
    - Inputs: proposal form fields + constraints
    - Output: eligibility checks + required revisions + next step

### Practical guides (Microsoft Platform + Copilot + “vibe coding”)

### Practical guide for students

- **Pick 1 workflow** (onboarding, helpdesk triage, scheduling, or intake) and define the *real case* you will improve (what fails today, and why).
- **Start with “vibe coding”, but with guardrails**:
    - Ask Copilot for a first draft of `docs/[system-map.md](http://system-map.md)` including **boundaries**, **actors**, **states**, **transitions**, **handoffs**, **failure points**, and **feedback loops**.
        - *Example prompt (Student onboarding workflow)*: “Draft `docs/[system-map.md](http://system-map.md)` for a student onboarding workflow. Include: system boundary, actors (student, advisor, registrar, LMS), states (Not started → In progress → Blocked → Complete), transitions, handoffs, failure points (missing docs, holds), and feedback loops (reminders, advisor follow-up). List explicit assumptions.”
    - Review the draft and correct assumptions. Every assumption must be explicit in the system map.
- **Turn the map into rules** (`docs/[rules-spec.md](http://rules-spec.md)`):
    - Produce at least **10 numbered rules** and **5 edge cases**.
        - *Example prompt (Helpdesk triage workflow)*: “From this helpdesk triage system map, generate `docs/[rules-spec.md](http://rules-spec.md)` with 10 numbered routing rules and 5 edge cases. For each rule include Input, Condition, Output (queue + SLA), and a user-facing message. Edge cases must include: ambiguous category, conflicting urgency signals, missing requester info, duplicate tickets, and after-hours submissions.”
    - For each rule, include: **Input**, **Condition**, **Output**, and a **UX message** (what you tell the user when the rule applies or fails).
- **Prototype fast (repo must be runnable)**:
    - Implement a minimal prototype (CLI / API / small web UI) in `src/` that takes sample inputs and returns a decision.
        - *Example prompt (Appointment scheduling workflow)*: “Create a minimal runnable prototype (CLI) in `src/` for appointment scheduling. Input: a JSON file with availability blocks, constraints, and priorities. Output: proposed schedule plus explanations for conflicts. Include structured logs that state which rule was applied.”
    - Your output must include a **“why/explanation”** (example: “Routed to X due to Rule 3 under Condition Y”).
- **Close the loop with tests** (`tests/`):
    - Write tests for the **happy path**, **edge cases**, and **failure cases**.
        - *Example prompt (Course project intake workflow)*: “Generate tests for a course project intake eligibility checker. Cover happy path, 5 edge cases, and failure cases. Edge cases: missing prerequisite, GPA exactly at threshold, late submission boundary time, conflicting form answers, and incomplete attachments. For each test, assert both the decision and the explanation text.”
    - Every edge case in the spec must have at least one test that validates it.
- **GitHub evidence (graded behaviors)**:
    - Create issues early (include at least 2 edge-case issues and 1 UX wording/interaction issue).
    - Work through PRs that reference issues and include test notes.
    - Maintain a `CHANGELOG` that explains **what changed and why**.
    - Tag releases: `v0.1` (map + spec + runnable skeleton) and `v1.0` (tests + reflection + stable demo).

### GitHub repo setup guide (and README orientation)

- **1) Create the repository**
    - Create a new GitHub repo with a clear name (example: `workflow-prototype-helpdesk-triage`).
    - Add a `.gitignore` for your language (Node/Python/etc.).
    - Add a license if your instructor requires it.

- **2) Create the required folder structure**
    - Create these paths (even if some start empty):
        - `docs/`
        - `src/`
        - `tests/`
        - `data/` (optional, for sample inputs)
        - `.github/` (optional, for CI)

- **3) Add the core files early**
    - [`README.md`](http://README.md) (how to navigate + how to run)
    - `docs/[system-map.md](http://system-map.md)`
    - `docs/[rules-spec.md](http://rules-spec.md)`
    - `docs/[reflection.md](http://reflection.md)`
    - [`CHANGELOG.md`](http://CHANGELOG.md)

- **4) Use GitHub Issues as your work plan (graded)**
    - Create issues for:
        - System map draft + review
        - Rules spec + edge cases
        - Prototype skeleton
        - Tests for happy path
        - Tests for edge cases
        - UX wording / interaction messages
    - Add acceptance criteria to each issue (what “done” means).
- **5) Work through Pull Requests (graded)**
    - Create a branch per issue (example: `issue-03-prototype-skeleton`).
    - Open a PR early, then commit in small steps.
    - In the PR description include:
        - What changed
        - How to test (commands)
        - Evidence (screenshots/log snippets if relevant)
- **6) Add a minimal CI (optional but strong)**
    - Use GitHub Actions to run tests on every PR.
    - Keep it fast and simple (install deps → run unit tests).
- **7) Tag releases**
    - `v0.1`: system map + rules spec + runnable skeleton
    - `v1.0`: tests + reflection + stable demo

### Suggested repo structure (complete)

```
.
├── [README.md](http://README.md)
├── docs/
│   ├── [system-map.md](http://system-map.md)
│   ├── [rules-spec.md](http://rules-spec.md)
│   ├── [reflection.md](http://reflection.md)
│   └── [changelog.md](http://changelog.md)
├── src/
│   ├── [app.py](http://app.py)                     # or main entry point
│   ├── [rules.py](http://rules.py)
│   └── ui/                        # optional
├── tests/
│   ├── test_rules_happy_[path.py](http://path.py)
│   ├── test_rules_edge_[cases.py](http://cases.py)
│   └── test_rules_[failures.py](http://failures.py)
├── examples/
│   ├── input_normal.json
│   ├── input_edge.json
│   └── input_failure.json
├── requirements.txt               # or environment.yml
├── .gitignore
└── assets/
    └── diagrams/
```

---

### Evaluation rubric (simple)

- **Systems model quality (25%)**: boundary, actors, states, failure modes are clear.
- **Rule clarity & correctness (25%)**: spec is testable; edge cases handled.
- **UX clarity (25%)**: outputs are understandable; uncertainty/failures are communicated.
- **Evidence & workflow (25%)**: repo is runnable, documented, and shows decision evolution.

---

### Stretch goals

- Add property-based tests for rule correctness.
- Add a minimal UI for rule inspection and “why” explanations.
- Add containerization or a simple deployment plan.
- Add observability notes: what metrics would be tracked in production.

<aside>
🧾

**Portfolio note**: Strong submissions read like a workflow handoff: system map + rules spec + runnable prototype + tests + reflection.

</aside>