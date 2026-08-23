# Web Developer Academy — Curriculum Phases

Reference curriculum for the academy. Adjust pacing based on `progress-tracker.md`, but preserve
prerequisites and depth — see `CLAUDE.md` for how to teach this, not just what.

## Career-direction change (2026-08-23) — final

This curriculum was originally designed around a Cloud Engineer target, then pivoted to SDET /
QA Automation on 2026-07-29. On 2026-08-23 the target changed again to **Web Developer with Front
End and Back End experience** (full-stack). Juan has stated this is his definitive direction and
no further career-direction changes are expected. See `progress-tracker.md` for the full decision
record and how prior work transfers.

**Circumstances this plan is paced against** (confirmed 2026-08-23, revisit only if they
change): study time ~2-3 hrs/day, Monday-Friday; programming background is CS50-only; English is
conversational and still building technical vocabulary; based in Florida, USA, with a work
permit and citizenship pending (no visa sponsorship needed for US remote roles); training budget
roughly $200-1000 total, not recurring.

## What carries over from the SDET plan

- **Retained as core, already in progress:** Git and GitHub fundamentals (branching, PRs, commit
  discipline, recovery from mistakes), Linux/command-line fundamentals, and JavaScript/
  TypeScript fundamentals. These are direct prerequisites for web development (every phase below
  depends on them) — continue them, don't redo them.
- **Retained, reframed from testing to building:** HTML/CSS/browser DevTools (was "find stable
  locators for testing," now "build real pages and debug them"), SQL/databases (was "verify
  application state after a test," now "design and query the data behind your own app"), REST/
  HTTP fundamentals (was "test an API," now "build an API"), GitHub Actions/CI/CD, Docker basics.
- **Kept but made lightweight:** automated testing. A working web developer needs to write unit
  and basic end-to-end tests for their own code, but doesn't need SDET-level depth (test
  architecture, flaky-test root-causing, dedicated a11y/perf/security audit tooling). See Phase 8.
- **Removed entirely:** the SDET-specific deep phases — dedicated Playwright framework design
  (Page Object Model at professional depth), API-testing-as-a-specialty (auth/CRUD/permission
  matrices as an end in themselves), a dedicated test-architecture/flaky-test-elimination phase,
  and a dedicated accessibility/performance/security *testing* phase. None of these are
  load-bearing for a Front End / Back End developer role, and the time they'd cost competes
  directly with actually building and shipping applications, which matters more for this target.
- **Added, new for this target:** a front-end framework (React), back-end framework and API
  *building* (Node.js/Express), full-stack integration and authentication, and deployment/
  hosting — none of these existed in the SDET plan, which tested applications rather than built
  them.

## Certifications

No certificate is required to start applying for Web Developer roles. Portfolio projects and a
working GitHub history matter far more to hiring managers in this field than any certification.
Not a planned budget item unless a specific target job posting explicitly asks for one.

## Study allocation while CS50 is in progress

Roughly 30-40% of study time on CS50 (until it's finished), 60-70% on web-development-specific
material and portfolio work. The two tracks run in parallel, not sequentially — do not postpone
React/Node until CS50 finishes. CS50 topics feed directly into these phases as they're covered,
even more directly than under the SDET plan since CS50 itself teaches web technologies:

| CS50 topic | Feeds into |
|---|---|
| Algorithms and data structures | Problem-solving/interview prep (Phase 13); writing efficient client and server logic |
| C and memory | Debugging discipline and understanding program behavior under the hood |
| Python | General scripting fluency; conceptual bridge into Phase 5 (Node/Express) even though the runtime differs |
| SQL | Phase 6 (database design for applications) |
| HTML, CSS, JavaScript | Phases 3 and 4 directly (front-end fundamentals and React) |
| Flask | Direct backend-framework analogue for Phase 5 (Node/Express); the CS50 final project becomes the literal seed for the Phase 12 capstone |

Academic honesty: AI/mentor support helps Juan understand concepts, debug his own reasoning, and
identify mistakes in CS50 problem sets — it does not write or complete CS50 problem sets for him,
per CS50's academic honesty policy. The CS50 final project is treated as a development project
that, once CS50 is done, can be extended into (or directly become) a Phase 12 portfolio project.

---

## Phase 1 — Git and GitHub foundations (retained, in progress)

**Learn:** repositories, staging, commits, history, diffs, branches, merging, remotes,
push/pull, `.gitignore`, README files, merge conflicts, recovery from mistakes (`reset`,
`revert`, `reflog`, `commit --amend`), rebase vs. merge, professional commit messages, pull
requests, merge strategies.

**Practice:** everything above hands-on, on real branches, including recovering from real
(not staged) mistakes.

**Produce:** `handbook/git.md` reference notes in Juan's own words; clean PR history on this
repo.

**Ready to advance when:** Juan can explain reset (soft/mixed/hard) vs. revert vs. amend
vs. rebase unprompted, and can diagnose a diverged-branches situation without being walked
through it.

**Status:** Days 001-010 complete, including rebase vs. merge. Readiness bar met as of Day 009;
rebase/merge practiced on Day 010. Advance to Phase 2 as of Day 011.

---

## Phase 2 — JavaScript and TypeScript fundamentals

**Learn:** values/types, variables, functions, control flow, arrays/objects, `async`/`await`
and promises, modules (`import`/`export`), `npm`/`package.json`, basic TypeScript types and why
static typing helps at application scale (catching a wrong prop type or a bad API response shape
at compile time instead of in production).

**Practice:** small standalone scripts; deliberately translate a few CS50 Python exercises into
TypeScript once the underlying logic is already understood (reinforces the concept without
re-teaching it, and builds TS fluency against something already correct).

**Produce:** a handful of small utility scripts in the repo, each with a short note on what it
does and why a type was chosen the way it was.

**Ready to advance when:** Juan can read a TypeScript compiler error and identify the fix without
pasting it into an AI first.

**Status:** Current phase as of Day 011 (see `progress-tracker.md` for exact resume point).

---

## Phase 3 — HTML, CSS, and front-end fundamentals

**Learn:** semantic HTML, the DOM, common elements/attributes (forms, buttons, labels, ARIA
attributes), CSS selectors and specificity, the box model, Flexbox and Grid for layout,
responsive design (media queries, mobile-first), and the browser DevTools panels used for
building and debugging: Elements (inspect/edit live DOM), Console, Network (inspect requests/
responses), and Application (storage/cookies).

**Practice:** build real static pages by hand (no framework yet) — a multi-section layout with
Flexbox/Grid, a responsive nav that collapses on mobile, a form with proper labels/validation
attributes. Use DevTools to debug layout issues rather than guessing.

**Produce:** two or three small static pages/components in the repo, plus short notes on layout
decisions (why Flexbox vs. Grid for a given layout, why a given breakpoint).

**Ready to advance when:** Juan can build a responsive multi-section page from a rough mockup
without copying a template, and can debug a layout issue using DevTools rather than trial-and-
error CSS edits.

---

## Phase 4 — React and front-end application development

**Learn:** components, JSX, props, state (`useState`), effects (`useEffect`), conditional
rendering, lists and keys, forms and controlled inputs, basic client-side routing, and fetching
data from an API on the client.

**Practice:** build a small multi-view single-page app (e.g. a to-do app with persistence, or a
small dashboard consuming a public API) — component composition, state lifting, and handling
loading/error states from real network requests.

**Produce:** a React app in the repo (or its own repo, linked from here), organized into
reusable components, with a short architecture note on how state flows through it.

**Ready to advance when:** Juan can explain why a piece of state lives where it does (component
vs. lifted to a parent) and can add a new feature to an existing component tree without breaking
unrelated parts.

---

## Phase 5 — Node.js, Express, and REST API development

**Learn:** the Node.js runtime and module system, building a REST API with Express (routes,
middleware, request/response handling), HTTP methods and status codes from the *building* side,
request validation, authentication patterns (sessions/JWTs), error handling, and connecting a
server to a database (Phase 6).

**Practice:** build a real API from scratch — CRUD endpoints, input validation, meaningful error
responses (not just 500 for everything), and at least one protected route requiring
authentication.

**Produce:** an Express API in the repo with a README documenting its endpoints, committed with
a clean PR.

**Ready to advance when:** Juan can add a new authenticated CRUD endpoint to an existing API
without a tutorial open next to him, and can explain what each middleware in his stack does.

---

## Phase 6 — SQL and database design for applications

**Learn:** SQL fundamentals (reinforcing CS50's SQL week, not re-teaching from scratch) —
`SELECT`/`JOIN`/`WHERE`/constraints — plus schema design for a real application: normalization
basics, primary/foreign keys, and choosing a database (SQLite for learning, Postgres for
anything meant to be deployed).

**Practice:** design and build the schema for the Phase 5 API's data (e.g. users, posts,
relationships between them), write the queries the API actually needs, and connect it via a
lightweight query builder or ORM.

**Produce:** a schema (with a simple ER diagram or written description) and the queries/
migrations backing the Phase 5 API.

**Ready to advance when:** Juan can design a reasonable schema for a new feature and write the
queries it needs without a tutorial open next to him.

---

## Phase 7 — Full-stack integration and authentication

**Learn:** connecting a React front end to an Express/SQL back end end-to-end: environment-based
API URLs, CORS, real authentication flow (login, session/token storage, protected routes on both
client and server), and handling loading/error/empty states consistently across a real app.

**Practice:** take the Phase 4 front end and Phase 5/6 back end and wire them together into one
working full-stack app with real login, not separate disconnected pieces.

**Produce:** a working full-stack app (front end + back end + database) with real
authentication, committed with a clean PR history.

**Ready to advance when:** Juan can trace a single user action (e.g. submitting a form) through
the entire stack — client state, network request, server validation, database write, response,
UI update — and explain each step.

---

## Phase 8 — Testing fundamentals for web applications (lightweight)

**Learn:** why testing exists and what it costs to skip it; unit testing basics (Jest or
Vitest) for both front-end components and back-end logic; basic end-to-end smoke testing
(Playwright) for critical user flows only — not a full test-architecture specialization.

**Practice:** write unit tests for a handful of meaningful functions/components in the Phase 7
app, and one or two E2E smoke tests covering its most critical flow (e.g. login → core action).

**Produce:** a test suite (unit + a small number of E2E tests) attached to the Phase 7 app.

**Ready to advance when:** Juan can write a reasonable unit test for a new function without
being walked through it, and understands what an E2E smoke test is for versus a unit test.

---

## Phase 9 — GitHub Actions, CI/CD, and Docker basics

**Learn:** workflow YAML structure, triggers (push/PR), running lint/build/test in CI, images vs.
containers, Dockerfiles, `docker-compose` for a local multi-service stack (app + database), and
why containerizing makes both CI and onboarding reproducible.

**Practice:** wire the Phase 8 test suite (and a build step) into GitHub Actions on the Phase 7
app; containerize the app and its database with Compose so the whole stack runs with one command.

**Produce:** a green CI badge on the app's repository, plus a working `docker-compose.yml`.

**Ready to advance when:** a broken build/test fails CI and Juan can identify why from the CI
logs without re-running it locally first, and can explain what each service in the compose file
does.

---

## Phase 10 — Deployment and hosting

**Learn:** deploying a front end (e.g. Vercel/Netlify), deploying a back end + database (e.g.
Render/Railway/Fly.io), environment variables and secrets in production, production vs.
development builds, and basic custom-domain/HTTPS concepts.

**Practice:** deploy the Phase 7-9 app end-to-end so it's reachable at a real public URL, with
environment variables configured correctly for the production database and API.

**Produce:** a live, publicly accessible deployment of a real portfolio project, linked from its
README.

**Ready to advance when:** Juan can deploy a new change (front end or back end) himself and
diagnose a failed deploy from platform logs without guessing.

---

## Phase 11 — Accessibility and performance fundamentals

**Learn:** building accessible UI by default (semantic HTML, keyboard navigation, sufficient
color contrast, ARIA only where semantic HTML isn't enough), and basic performance practices
(image optimization, code splitting/lazy loading, avoiding unnecessary re-renders in React,
reading a Lighthouse report).

**Practice:** run Lighthouse and an automated a11y check (axe-core) against a Phase 7-10 app,
then fix what they surface — not just note it.

**Produce:** a short before/after note in the app's README describing what was fixed and why it
mattered to a real user.

**Ready to advance when:** Juan can explain one real accessibility or performance fix in terms
of user impact, not just "the scanner flagged it."

---

## Phase 12 — Portfolio projects

Three required projects, each meeting the bar below before it counts as "portfolio-ready":

1. **Front-end project** — a polished React app with real UX (loading/error/empty states,
   responsive design, reasonably accessible), consuming either a public API or the Phase 5 API.
2. **Back-end/API project** — a well-documented REST API with authentication, real data
   validation, and a real database behind it (separate from, or reused from, Phase 5-6).
3. **Capstone** — a full-stack app combining front end, back end, and database (ideally the CS50
   final project extended, or the Phase 7-11 app taken further), deployed live, with CI, tests,
   and — if appropriate — Docker.

Every repository needs: a professional README, setup instructions, an architecture explanation,
a live deployed link where applicable, and visible CI results (badge/link). None of the three
counts as done until Juan can discuss it cold in an interview — expect iteration rounds on each,
not a single pass.

---

## Phase 13 — Employment preparation (parallel track, once the foundation is solid)

Starts once Phase 7 is demonstrated and at least one portfolio project exists — not held until
everything else is finished, but not started before there's real work to present either.

**Covers:** GitHub portfolio presentation, résumé language for a non-degree candidate, Front
End / Back End / Full Stack interview questions (conceptual and coding), whiteboard/live-coding
practice, debugging exercises, explaining architectural decisions out loud, evaluating real job
descriptions, and identifying remote-first employers.

**Specifically practice screening job postings for:** on-call requirements, activity-monitoring
software mentions, excessive-meeting culture signals, and roles whose actual day-to-day doesn't
match the title — so Juan can filter these out himself before applying, not discover them after
accepting an offer.

**Realistic progression** (not a promise, a likely path): portfolio-ready beginner → first Front
End or Back End developer role (entry point, whichever the portfolio and interviews favor) →
Full Stack Developer, typically over multiple years of real work experience, not a fast track
from a short course. $100k+ is a plausible mid-level outcome over time, not a first-job
expectation.

**Target roles, in order of initial focus:** Front End Developer and Back End Developer (either
is an acceptable entry point depending on which interviews land first), Full Stack Developer
(primary longer-term target as experience builds across both sides).

---

## Professional habits reinforced throughout

Clear written communication; technical English; accurate terminology; careful reading;
documentation use; note-taking; command-line confidence; Git discipline; troubleshooting;
writing readable, maintainable code (naming, security, reliability); asking precise questions;
explaining assumptions; testing before concluding; verifying outputs; recognizing uncertainty;
avoiding random changes; writing useful documentation; finishing and maintaining projects.
