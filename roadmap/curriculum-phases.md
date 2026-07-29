# SDET / QA Automation Academy — Curriculum Phases

Reference curriculum for the academy. Adjust pacing based on `progress-tracker.md`, but preserve
prerequisites and depth — see `CLAUDE.md` for how to teach this, not just what.

## Career-direction change (2026-07-29)

This curriculum was originally designed around a Cloud Engineer target. On 2026-07-29 the
target changed to **SDET / Test Automation Engineer / QA Automation Engineer**, based on Juan's
priorities: fully remote, good work-life balance, predictable hours with no production on-call,
independent outcome-based work, skills-and-portfolio accessible (no degree required), and
long-term $100k+ potential. See `progress-tracker.md` for the full decision record and how prior
work transfers.

**Circumstances this plan is paced against** (confirmed 2026-07-29, revisit if they change):
study time ~2-3 hrs/day, Monday-Friday; programming background is CS50-only; English is
conversational and still building technical vocabulary; based in Florida, USA, with a work
permit and citizenship pending (no visa sponsorship needed for US remote roles); training budget
roughly $200-1000 total, not recurring.

## What carries over from the Cloud Engineer plan

- **Retained as core, already in progress:** Git and GitHub fundamentals (branching, PRs, commit
  discipline, recovery from mistakes), Linux/command-line fundamentals. These are direct
  prerequisites for SDET work (test-code repos, CI triggers, debugging environments) — continue
  them, don't redo them.
- **Retained, postponed, made lightweight:** cloud fundamentals (enough to understand a
  cloud-hosted application under test — not a certification track). Revisit only if a target job
  posting specifically calls for AWS/GCP/Azure exposure.
- **Removed entirely:** Terraform/Infrastructure as Code, Kubernetes, deep networking
  (subnetting, routing, firewalls, load balancers as a dedicated topic), observability/SRE
  material, and all three AWS certifications (Cloud Practitioner, Solutions Architect, SysOps).
  None of these are load-bearing for SDET/QA Automation roles, and cert-prep time competes
  directly with portfolio time, which matters more for this target.
- **Reframed, not removed:** networking basics survive only as much as HTTP/TLS/DNS/status codes
  needed to understand what your automated tests are actually talking to (Phase 6).

## Certifications

No certificate is required to start applying. ISTQB Foundation (CTFL) has resume-screening value
at some companies but is not worth the time before the portfolio exists. Revisit only if a
specific job posting you're targeting explicitly asks for it, and only spend budget on it after
Phase 12's projects are credible — a cert without a portfolio behind it doesn't move the needle
for this target role.

## Study allocation while CS50 is in progress

Roughly 30-40% of study time on CS50 (until it's finished), 60-70% on SDET-specific material and
portfolio work. The two tracks run in parallel, not sequentially — do not postpone Playwright and
automation until CS50 finishes. CS50 topics feed directly into SDET phases as they're covered:

| CS50 topic | Feeds into |
|---|---|
| Algorithms and data structures | Problem-solving / interview prep (Phase 13) |
| C and memory | Debugging discipline and understanding program behavior under the hood |
| Python | Scripting and API utility scripts (Phase 6 support) |
| SQL | Phase 7 (database validation) |
| HTML, CSS, JavaScript | Phases 3 and 5 (browser fundamentals, Playwright) |
| Flask | Understanding client-server/API behavior (Phase 6), and the basis for the capstone app |

Academic honesty: AI/mentor support helps Juan understand concepts, debug his own reasoning, and
identify mistakes in CS50 problem sets — it does not write or complete CS50 problem sets for him,
per CS50's academic honesty policy. The CS50 final project is treated as a development project
that later becomes the target of a testing/automation portfolio project (Phase 12), not as SDET
coursework itself.

---

## Phase 1 — Git and GitHub foundations (retained, nearly complete)

**Learn:** repositories, staging, commits, history, diffs, branches, merging, remotes,
push/pull, `.gitignore`, README files, merge conflicts, recovery from mistakes (`reset`,
`revert`, `reflog`, `commit --amend`), professional commit messages, pull requests, merge
strategies.

**Practice:** everything above hands-on, on real branches, including recovering from real
(not staged) mistakes — this is already how Days 006-009 have gone.

**Produce:** `handbook/git.md` reference notes in Juan's own words; clean PR history on this
repo.

**Ready to advance when:** Juan can explain reset (soft/mixed/hard) vs. revert vs. amend
unprompted, and can diagnose a diverged-branches situation without being walked through it.

**Status:** Days 001-008 complete. Day 009 in progress — see `progress-tracker.md` for the exact
resume point (an independent challenge on choosing between `--amend` and `reset` + recommit).

---

## Phase 2 — TypeScript and JavaScript fundamentals

**Learn:** values/types, variables, functions, control flow, arrays/objects, `async`/`await`
and promises, modules (`import`/`export`), `npm`/`package.json`, basic TypeScript types and why
static typing matters for test code specifically (catching a bad selector or wrong argument at
compile time instead of at 2am in CI).

**Practice:** small standalone scripts; deliberately translate a few CS50 Python exercises into
TypeScript once the underlying logic is already understood (reinforces the concept without
re-teaching it, and builds TS fluency against something already correct).

**Produce:** a handful of small utility scripts in the repo, each with a short note on what it
does and why a type was chosen the way it was.

**Ready to advance when:** Juan can read a TypeScript compiler error and identify the fix without
pasting it into an AI first.

---

## Phase 3 — HTML, CSS, and browser developer tools

**Learn:** DOM structure, common HTML elements/attributes relevant to testing (forms, buttons,
labels, ARIA attributes), CSS selectors and specificity basics, the box model, and the browser
DevTools panels that matter for testing: Elements (inspect/edit live DOM), Console, Network
(inspect requests/responses), and Application (storage/cookies).

**Practice:** open real websites, find elements by hand using DevTools, write CSS/XPath-style
selectors without a recorder tool, watch real network requests fire during normal browsing.

**Produce:** short notes on selector strategy (why `data-testid` or accessible roles are
preferred over brittle CSS chains).

**Ready to advance when:** Juan can find a reasonably stable locator for a given element on an
unfamiliar page without guessing-and-checking in a recorder.

---

## Phase 4 — Software testing principles (~30% theory ceiling for this phase)

**Learn:** why testing exists and what it costs to skip it; the test pyramid (unit/integration/
E2E) and where automation fits; black-box test design (equivalence partitioning, boundary value
analysis); positive vs. negative test cases; test case structure; what makes a good bug report
(steps to reproduce, expected vs. actual, environment, severity).

**Practice:** given a real feature (a login form, a search box), design a test-case set by hand
before writing any code — this is deliberately code-free to build the design skill
independently of tool fluency.

**Produce:** a written test-case document for a real site/feature, plus one properly written bug
report for a real bug Juan finds.

**Ready to advance when:** Juan can justify *why* a specific test case exists (what risk it
covers), not just produce a list of steps.

---

## Phase 5 — Playwright fundamentals (TypeScript)

**Learn:** Playwright project setup and config, locators (role-based, text, `data-testid`),
actions (click, fill, navigate), assertions (`expect`), the Page Object Model, fixtures, running
tests headed/headless, and reading a failed test's trace/screenshot/video output.

**Practice:** automate a real multi-step workflow (e.g. login → search → add to cart →
checkout) end to end, including at least one negative-path test (invalid login, empty required
field).

**Produce:** first real Playwright test file(s), organized with a Page Object Model, committed
with a clean PR.

**Ready to advance when:** the suite passes reliably across at least 3 consecutive runs with no
`waitForTimeout` hacks and no manual re-runs to "make it pass."

---

## Phase 6 — API and HTTP testing

**Learn:** REST fundamentals, HTTP methods and status codes, authentication patterns (tokens/
cookies/API keys), request/response schema validation, and Playwright's built-in API testing
support (or a lightweight HTTP client library).

**Practice:** test a real API (public API or one built with Flask from CS50) — CRUD operations,
authorization/permission checks (what happens when you're not allowed to do something), and
error-handling cases, not just the happy path.

**Produce:** an API test suite covering auth, CRUD, permissions, and error responses, with
assertions on both status codes and response bodies.

**Ready to advance when:** Juan can explain, from his own tests, the practical difference between
a 401, a 403, and a 422 — not just recite the definitions.

---

## Phase 7 — SQL and database validation

**Learn:** SQL fundamentals (reinforcing CS50's SQL week, not re-teaching from scratch) —
`SELECT`/`JOIN`/`WHERE`/constraints — from the specific angle of verifying application state
after a UI or API action.

**Practice:** after a test performs an action (e.g. creates a user via the API), query the
database directly to confirm the expected row/state exists, rather than trusting the API
response alone.

**Produce:** database assertion helpers used inside the Phase 5/6 test suites.

**Ready to advance when:** Juan can write a verification query for a new scenario without a
tutorial open next to him.

---

## Phase 8 — GitHub Actions and CI/CD

**Learn:** workflow YAML structure, triggers (push/PR), running a test suite in CI, artifacts
(reports, traces, screenshots on failure), matrix runs across browsers.

**Practice:** wire the Phase 5 and Phase 6 suites into GitHub Actions on this repo (or a
project repo), including a deliberately broken test to see a red CI run and diagnose it from
logs alone.

**Produce:** a green CI badge on a real repository, with a workflow file Juan can explain
line by line.

**Ready to advance when:** a broken test fails CI and Juan can identify why from the CI logs
without re-running it locally first.

---

## Phase 9 — Docker basics

**Learn:** images vs. containers, Dockerfiles, `docker-compose` for multi-service local stacks
(app + database), why containerizing the app-under-test makes CI reproducible.

**Practice:** containerize a small app (ideally the CS50 final project) plus its database with
Compose, and point the Phase 5-7 test suites at the containerized stack instead of a manually
run dev server.

**Produce:** a working `docker-compose.yml` used by the CI workflow from Phase 8.

**Ready to advance when:** Juan can explain what each service in the compose file does and why
it's configured that way, without reading it off a tutorial.

---

## Phase 10 — Test architecture and eliminating flaky tests

**Learn:** fixtures and hooks for setup/teardown, test isolation and why shared state causes
intermittent failures, parallelization, and the real root causes of flaky tests — timing/race
conditions, network variability, environment differences, and test interdependence. Explicitly:
retries are a symptom-mask, not a fix, and should never be the first response to a flaky test.

**Practice:** deliberately introduce a flaky test (e.g. a race condition against an async UI
update), diagnose it using Playwright's trace viewer/video, and fix the root cause rather than
adding a retry or a sleep.

**Produce:** a short written "flaky test post-mortem" — what caused it, how it was diagnosed,
what the actual fix was.

**Ready to advance when:** given an unfamiliar flaky test, Juan can diagnose the likely cause
from a trace/video before touching the code.

---

## Phase 11 — Accessibility, performance, and security testing fundamentals

Only after Phases 5-10 are solid — this extends core automation skill, it doesn't replace it.

**Learn:** automated accessibility checks (axe-core integrated with Playwright), basic
performance signals (Lighthouse), and the OWASP Top 10 from a tester's perspective (what to
probe for, not how to build exploits).

**Practice:** add accessibility checks to an existing Phase 5 suite; run a basic performance
audit on a real page; identify (not exploit) one plausible security-testing consideration for a
target application.

**Produce:** an accessibility report section added to a portfolio project.

**Ready to advance when:** Juan can explain one real a11y finding and why it matters to a user,
not just that a scanner flagged it.

---

## Phase 12 — Portfolio projects

Three required projects, each meeting the bar below before it counts as "portfolio-ready":

1. **Playwright web-automation framework** — realistic multi-step user workflows, negative
   scenarios, multiple browsers, Page Object Model, CI-integrated.
2. **API-testing project** — authentication, CRUD, permissions/authorization checks, error
   handling, response/schema validation.
3. **Capstone** — combines web, API, and database testing against a real application (ideally
   the CS50 final project, built out with an API and database), running in GitHub Actions, with
   Docker if appropriate.

Every repository needs: a professional README, a written test strategy, setup instructions,
example bug reports, an architecture explanation, and visible CI results (badge/link). None of
the three counts as done until Juan can discuss it cold in an interview — expect iteration
rounds on each, not a single pass.

---

## Phase 13 — Employment preparation (parallel track, once the foundation is solid)

Starts once Phase 5-6 are demonstrated and at least one portfolio project exists — not held
until everything else is finished, but not started before there's real work to present either.

**Covers:** GitHub portfolio presentation, résumé language for a non-degree candidate, SDET/
automation interview questions (conceptual and coding), debugging exercises, test-design
exercises, explaining architectural decisions out loud, evaluating real job descriptions, and
identifying remote-first employers.

**Specifically practice screening job postings for:** on-call requirements, activity-monitoring
software mentions, excessive-meeting culture signals, and roles that are manual-testing-heavy
despite an "automation" title — so Juan can filter these out himself before applying, not
discover them after accepting an offer.

**Realistic progression** (not a promise, a likely path): portfolio-ready beginner → first
Test Automation Engineer role (entry point) → QA Automation Engineer → remote mid-level SDET /
Test Automation Engineer, typically over multiple years of real work experience, not a fast
track from a short course. $100k+ is a plausible mid-level outcome over time, not a first-job
expectation.

**Target roles, in order of initial focus:** Test Automation Engineer (primary initial target),
QA Automation Engineer (parallel target), SDET (longer-term target as experience builds).

---

## Professional habits reinforced throughout

Clear written communication; technical English; accurate terminology; careful reading;
documentation use; note-taking; command-line confidence; Git discipline; troubleshooting;
recognizing and eliminating flaky tests rather than tolerating them; treating test code as
production code (readability, maintainability, naming, security, reliability); asking precise
questions; explaining assumptions; testing before concluding; verifying outputs; recognizing
uncertainty; avoiding random changes; writing useful documentation; finishing and maintaining
projects.
