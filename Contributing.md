# Contributing to Springwell-Keel

LHB Social Enterprise | Apache-2.0

---

## Welcome

Springwell-Keel is a greenfield, open-source, agentic workflow orchestration framework powering three independent SaaS products from a single intelligent core. We are building in public, from day zero.

There is no legacy codebase. No inherited architecture decisions. No patterns already baked in. If you have been waiting for a project where you can shape the bones of a real agentic system before they calcify — the window is now.

---

## Before You Start

**Read First:**
- `README.md` — project overview and architecture
- `docs/adr` — Architecture Decision Records for major design choices
- `SECURITY.md` — responsible disclosure policy
- `CODE_OF_CONDUCT.md` — community standards

**Find Good First Issues:**
Issues tagged `good-first-issue` are scoped, documented, and ready. They are the right entry point for new contributors. Do not open a PR for work that is not tracked in an issue first.

---

## How to Contribute

### 1. Fork and Clone

```bash
git clone https://github.com/YOUR-USERNAME/springwell-keel.git
git remote add upstream https://github.com/lhb/springwell-keel.git
```

### 2. Create a Branch

Branch from `main`. Use a descriptive name:
- `feat/workflow-state-machine`
- `fix/agent-approval-gate`
- `docs/contributing-guide`

### 3. DCO Signoff — Required on Every Commit

All commits must include a Developer Certificate of Origin (DCO) signoff.

```bash
git commit --signoff -m "feat: add workflow state machine"
```

Or configure git to add `--signoff` automatically:

```bash
git config --global format.signOff true
```

Commits without signoff will not be merged. This is enforced.

### 4. Keep Your Branch Current

```bash
git fetch upstream && git rebase upstream/main
```

### 5. Open a Pull Request

- PR title: use conventional commit format (`feat:`, `fix:`, `docs:`, `chore:`)
- PR description: what does this change, why, and how was it tested
- Link the issue your PR addresses
- At least one reviewer approval required before merge
- CI must pass — lint, test, and build checks are required

---

## Architecture Decisions

Major decisions are documented as Architecture Decision Records (ADRs) in `/docs/adr`.

If you believe a core pattern should change, open a Discussion first. We use an RFC-based model — the best technical argument wins, not the loudest voice. Maintainer has final say during Phase 0–2.

---

## Subsystem Ownership

Contributors who demonstrate consistent, high-quality work on a subsystem will be invited to become subsystem owners — with real decision-making authority over that layer.

Subsystem ownership is documented in `CODEOWNERS`. It is earned, not assumed.

---

## What We Are Not Building Publicly

The Keel Engine judgment layer — scoring models, routing thresholds, and internal decision logic — is maintained privately by the core team. This is a deliberate architectural boundary documented from day zero.

Contributors build the engine, the interface, and the three lane environments. The internal reasoning layer is not part of this repo. This boundary will not change.

---

## Coding Standards

- **Language:** TypeScript (primary)
- **Formatting:** Prettier — enforced via CI
- **Linting:** ESLint — enforced via CI
- **Tests:** required for new features
- **Commits:** conventional commit format required
- **Comments:** explain why, not what

---

## Communication

- **Issues:** bugs, proposals, questions
- **Discussions:** architecture, direction, subsystem ownership
- **PRs:** code — link to the issue it addresses
- **Security:** see SECURITY.md — do not open public issues for vulnerabilities

---

*Built by LHB Social Enterprise | Apache-2.0 | Serving communities that need it most*
