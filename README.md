# System Map + Workflow Automation Prototype

> **Alignment**: Systems Thinking, Computational Logic, Human-Computer Interaction
> **Reference**: [Project Definition](docs/project_definition.md)

## Project Overview
Many operational failures come from unclear workflow rules, hidden assumptions, and poor handoffs. This project asks students to build a GitHub repo that:

- models a real workflow as a **system**
- defines a **rules specification** with edge cases
- implements a small prototype (CLI / web / API)
- includes tests and documentation so the workflow can be reviewed and improved

You will deliver:
- A clear **problem framing** and **decision boundary**
- An **ethical impact assessment** with mitigations
- A lightweight **prototype or simulation**
- Documentation of "intent" vs. "limitations"

## Scenario Options
Choose **one** of the following scenarios to base your project on.

### 1. Student onboarding workflow
- **Inputs**: student profile + required steps
- **Output**: next-step recommendations + completion status

### 2. Helpdesk triage workflow
- **Inputs**: ticket text + category + urgency signals
- **Output**: routing decision + SLA target + escalation rules

### 3. Appointment scheduling workflow
- **Inputs**: availability, constraints, priorities
- **Output**: proposed schedule + conflict explanations

### 4. Course project intake workflow
- **Inputs**: proposal form fields + constraints
- **Output**: eligibility checks + required revisions + next step

## Definition of Done (MVP)
A repo is considered "done" when:
- The decision scope is clear (what it DOES and DOES NOT do).
- Risks are documented with specific mitigations.
- A reviewer can run a demo (even if minimal).
- Limitations and failure modes are explicitly stated.

## How to Run

### 1. Local Setup
Ensure you have Python installed.

1.  **Clone the repository**
2.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the Prototype**:
    ```bash
    python src/app.py
    ```
4.  **Run Tests**:
    ```bash
    pytest
    ```

### 3. Automated Validation (CI/CD)
Every time you push a commit or open a Pull Request, **GitHub Actions** will automatically run the validation script.
- **✅ Pass**: Structure is correct and tests pass.
- **❌ Fail**: Missing requirements or failing tests.

## Required Deliverables

Your repository includes the following evidence artifacts (templates provided in `docs/`):

1.  **`README.md`** (This file, updated with your project specifics)
2.  **`docs/system-map.md`**: Boundaries, actors, states, and dependencies.
3.  **`docs/rules-spec.md`**: Numbered rules, edge cases, and UX messages.
4.  **`docs/reflection.md`**: Learning outcomes and improvements.
5.  **`CHANGELOG.md`**: Explanation of what changed and why.
6.  **Prototype**: A working script (`src/app.py`) with test cases.

## Project Structure
```
.
├── README.md
├── docs/
│   ├── system-map.md
│   ├── rules-spec.md
│   ├── reflection.md
│   ├── project_definition.md
│   └── changelog.md
├── src/
│   ├── app.py
│   └── rules.py
├── tests/
│   ├── test_rules_happy_path.py
│   ├── test_rules_edge_cases.py
│   └── test_rules_failures.py
├── examples/
│   ├── input_normal.json
│   ├── input_edge.json
│   └── input_failure.json
├── requirements.txt
└── .gitignore
```
