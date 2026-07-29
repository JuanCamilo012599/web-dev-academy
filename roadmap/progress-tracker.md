# SDET / QA Automation Academy - Progress Tracker

This file is the source of truth for my SDET / QA Automation Academy progress.
See `curriculum-phases.md` for the full phase-by-phase curriculum and
`../CLAUDE.md` for mentor/teaching instructions.

## Career Direction Update — 2026-07-29

Career target changed from Cloud Engineer to **SDET / Test Automation Engineer / QA Automation
Engineer**. Reasoning: fully remote work, good work-life balance, predictable hours with no
production on-call, independent outcome-based work, a path accessible via skills/certs/projects
without a university degree, and long-term $100k+ potential — SDET/test automation fits these
priorities better than the original cloud-infrastructure target.

**What transfers, unchanged:** all of Days 001-009 below. Git/GitHub (status, diff, add, commit,
branching, merging, remotes, PRs, commit conventions, merge strategies, reset/revert/reflog/
amend, cherry-pick) and Linux/command-line fundamentals are direct prerequisites for SDET work —
test-code repos go through the same PR review process, CI triggers off the same branches, and
recovering from a bad commit on a test suite uses the exact same tools practiced here. None of
Days 001-009 needs to be redone.

**What changed in the curriculum:** see `curriculum-phases.md` for the full revised phase
structure (Phase 1 Git/GitHub → Phase 13 employment prep) and its "What carries over from the
Cloud Engineer plan" section, which lists what was retained, postponed, or removed (Terraform,
Kubernetes, deep networking, observability, and all three AWS certifications were removed as not
load-bearing for this target; cloud fundamentals were kept but made lightweight and postponed).

**Circumstances confirmed 2026-07-29** (informs pacing — revisit if these change): study time
~2-3 hrs/day, Monday-Friday (previously included Saturday); programming background is CS50-only;
English is conversational, still building technical vocabulary; based in Miramar, Florida, USA,
with a work permit and citizenship pending — targeting US remote roles, no sponsorship needed;
training budget roughly $200-1000 total, not recurring. No certificate is being pursued yet (see
curriculum-phases.md "Certifications").

Note: on 2026-07-14 the learning system was restructured — mentor instructions
moved into `../CLAUDE.md`, the future curriculum moved into
`curriculum-phases.md`, and the handbook was split by topic. See
`../journal/day-006.md` for details. That journal entry, plus the "Fetch vs
Pull, and Handling Diverged Branches" section added to `handbook/git.md` on
the same day, were both drafted by the AI and transcribed rather than
independently written — flagged for a quick spaced-review check-in (verbal,
not written) at a later session, to confirm the fetch/pull/diverged/conflict
concepts actually stuck.

## Completed Classes

### Day 001 - Linux Setup and Navigation

Status: Completed

Main topics:
- Installed Python
- Verified pip
- Installed Git
- Set up GitHub
- Installed WSL with Ubuntu
- Entered Linux for the first time
- Learned basic Linux navigation
- Created the Cloud Engineer Academy folder structure
- Created the Handbook and Journal
- Made the first Git commit

Journal:
- journal/day-001.md

Handbook:
- handbook/linux.md

---

### Day 002 - Working With Files in Linux

Status: Completed

Main topics:
- touch
- cat
- echo
- cp
- mv
- rm
- nano
- Created Linux file practice project
- Completed Linux file challenge
- Made Git commits for file practice and challenge

Journal:
- Added as "Day 2 Update" inside journal/day-001.md

Handbook:
- handbook/linux.md

Project:
- projects/linux-file-practice

---

### Day 003 - Git Fundamentals

Status: Completed

Main topics:
- README.md
- git status
- git diff
- git diff --staged
- git add
- git commit
- git log --oneline --graph
- git restore
- .gitignore
- Clean commit habits

Journal:
- Pending

Handbook:
- handbook/git.md

---

### Day 004 - GitHub Connection

Status: Completed

Main topics:
- Local repository vs remote repository
- GitHub repository setup
- SSH key generation
- SSH authentication with GitHub
- git remote -v
- git remote set-url origin
- git push -u origin main
- origin/main

Journal:
- journal/day-004.md

Handbook:
- handbook/git.md

Remote repository:
- github.com/JuanCamilo012599/sdet-academy (renamed from cloud-engineer-academy on 2026-07-29)

---

### Day 005 - GitHub Workflow and Sync

Status: Completed

Main topics:
- git pull
- git push
- origin/main
- local branch vs remote branch
- syncing local and remote repositories
- clean GitHub workflow

Journal:
- journal/day-005.md

Handbook:
- handbook/git.md

---

### Day 006 - Pulling Remote Changes and Merge Conflicts

Status: Completed

Main topics:
- Editing files directly on GitHub.com
- git fetch vs git pull
- Reading ahead / behind / diverged in git status
- Fast-forward pull
- Forcing a diverged history on purpose
- git pull --no-rebase (merge vs rebase vs ff-only)
- Reading and resolving conflict markers
- Completing a merge commit
- Mistake: edited locally instead of on GitHub, fixed with git restore

Assessment:
- Fetch/pull, ahead/behind/diverged, live conflict resolution: Practiced
- Handbook and journal writeups for this day: AI-drafted, needs review

Journal:
- journal/day-006.md

Handbook:
- handbook/git.md ("Fetch vs Pull, and Handling Diverged Branches")

---

## Completed Classes (continued)

### Day 007 - Branching in Git

Status: Completed

Covered:
- Spaced-review check-in on Day 006 concepts (fetch vs pull, diverged branches,
  conflict markers) before starting new material. Mostly solid; corrected one
  nuance — divergence is about commit history branching (both sides committed
  separately), not necessarily about the same lines changing. Conflict is a
  possible *consequence* of divergence, not the same thing.
- Why branches exist: walked through the concrete cost of committing straight
  to main (teammates pulling broken/unfinished work, blocked until it's fixed;
  worse if main auto-deploys to prod).
- git branch (no args) - lists branches, `*` marks current (HEAD).
- git branch <name> - creates a branch without switching to it.
- git switch <name> - moves HEAD to a branch (noted git checkout is the older,
  more overloaded equivalent).
- Demonstrated branch isolation directly: created `day-007-branching`, added
  and committed `branch-test.md` there, confirmed the file does NOT exist back
  on `main` until merged.
- git merge <name> - performed a fast-forward merge (day-007-branching into
  main, no divergence so no merge commit needed). Explained why Git could
  fast-forward here vs. the real merge commit from Day 006.
- git branch -d <name> - safe delete (refuses if unmerged); contrasted with
  -D (force delete, can lose unreachable commits) - discussed but not run.
- Full remote branch lifecycle on a second practice branch
  (`day-007-remote-practice`): created, switched, committed a file, pushed
  with `git push -u origin <branch>` (observed upstream tracking get set
  up), verified it appeared on GitHub via `git branch -a`, merged into main
  (another fast-forward), pushed `main`, then deleted the branch both
  locally (`git branch -d`) and on GitHub (`git push origin --delete`), and
  confirmed with `git branch -a` that only `main`/`origin/main` remained.
  Correctly predicted the final `git branch -a` output before running it.
- Teach-back: explained the full create → switch → merge → delete lifecycle
  unprompted. Correct on branch isolation and roughly right on fast-forward
  ("no divergence") and on deleting merged branches; both refined slightly
  (fast-forward specifically because `main` hadn't moved at all since the
  branch was created; deleting a merged branch is safe because its commits
  already live permanently in main's history — the branch name was just a
  temporary pointer).
- Local repo state at end of session: `main` up to date with `origin/main`,
  both practice branches deleted locally and remotely, working tree has
  only handbook/tracker doc edits pending commit.

Documentation note (flagged, same as Day 006): first draft of the
`## Branching in Git` section in `handbook/git.md` was written by
transcribing the mentor's dictated explanation almost verbatim rather than
independently — caught and named directly this session rather than let
slide. Agreed compromise: factual command definitions (branch/switch/merge/
-d/-D/push -u/push --delete) may stay as accurate reference notes; the two
conceptual entries (**why branches exist**, **fast-forward vs. merge
commit**) still need to be rewritten by Juan from his own teach-back
sentences (which were already correct in substance, just incomplete) rather
than from the mentor's fuller paragraph. Not done yet — deferred to next
session at Juan's request. Flagged for a quick spaced-review check-in
(verbal, not written) alongside the existing Day 006 flag.

Journal: Pending (not yet written for this day)
Handbook: `handbook/git.md` has a `## Branching in Git` section, but the two
conceptual entries need the from-scratch rewrite described above before
they should be considered done.

---

### Day 008 - Professional Commit Messages and Pull Requests

Status: Completed

Pre-class check: confirmed Day 007's deferred items were done before
starting new material — `journal/day-007.md` was written (independently,
includes a genuine mistake/reflection), and the two conceptual
`handbook/git.md` entries ("Why branches exist", fast-forward vs. merge
commit) had been rewritten in Juan's own words. Verified by reading both
files, not just taking his word for it.

Spaced-review check-in (verbal, before new material):
- Fetch vs. pull: correct, no issues.
- "Diverged" — first answer repeated the Day 007 misconception ("a
  conflict between lines"). Corrected again: diverged = both sides have
  unique commits in their history; conflict is a possible *consequence*
  only if the same lines changed. Second attempt ("if changes are on
  different lines you can diverge with no conflict") was correct — held up
  under a follow-up question, not just recited.
- Fast-forward vs. merge commit (Day 007): correct ("main hasn't moved
  since I created the branch").

Covered:
- `man git-commit` DISCUSSION section: summary line ≤50 chars, and why
  Git treats the text before the first blank line as the commit "title"
  (used standalone in `git log --oneline`, GitHub UI, `git-format-patch`).
- Commit message convention practiced live: staged a real change, wrote
  the summary line himself (`Add test line to git.md`), committed.
  Confirmed lowercase-vs-capitalized first-letter is a per-project style
  choice, not a Git rule (his stated preference: lowercase).
- Pull requests: purpose (review before merging into `main`, vs. `git
  merge` which is a local, unreviewed operation) via GitHub's "About pull
  requests" doc. Confirmed understanding: a PR compares a base branch and
  a compare branch.
- Documentation integrity catch (recurring pattern, 3rd occurrence after
  Day 006/007): first draft of the "What's a pull request?" handbook entry
  was copied near-verbatim from GitHub's docs (the draft-PR paragraph
  specifically, which also showed a conceptual mix-up — describing draft
  PRs, not PRs in general). Rejected twice; third attempt was genuinely his
  own words and conceptually correct.
- Full PR lifecycle hands-on: created `day-008-pr-practice`, committed,
  pushed with `git push -u origin <branch>`, opened a real PR on GitHub
  (`#1`), reviewed the diff via the "Files changed" tab, explained the
  three merge-strategy options (merge commit / squash / rebase — rebase
  discussed but not used), chose squash-and-merge with reasoning (one
  commit on the branch was a meaningless placeholder).
- Unplanned real mistake, used as a live teaching moment: an earlier
  commit (`add test line to git.md`) had been made directly on local
  `main` instead of on a branch — the exact anti-pattern from Day 007.
  After the PR squash-merged, local `main` and `origin/main` showed as
  diverged. Diagnosed together (not handed the answer): squash-merge
  creates a brand-new commit with no ancestry link to the original
  branch commits, so the local-only commit and the new squashed commit on
  `origin/main` had overlapping content but zero shared history. Verified
  with `git show origin/main:handbook/git.md` that nothing local was
  unique before recovering with `git reset --hard origin/main` (Juan ran
  it himself, understood why it was safe in this specific case before
  running it).
- Real gotcha caught during branch cleanup: `git branch -d
  day-008-pr-practice` did not refuse to delete despite the branch's
  commit not being an ancestor of `main` post-squash — it warned instead
  of refusing, because `-d`'s safety check compares against the branch's
  own upstream, not against `main`. Flagged explicitly as "not a reliable
  safety net after a squash-merge."
- Handbook (`handbook/git.md`) updated by Juan: commit message convention,
  and all three merge strategies (rebase marked explicitly "not practiced
  yet"), all in his own words after one rejected copy/dictation attempt.

Process change agreed for journal-writing (going forward): Juan asked to
revert to an AI-drafted-narrative pattern for journals, referencing Day 006
as "the perfect balance." Corrected using the actual tracker record — Day
006's journal and Day 007's handbook section were both flagged as
AI-drafted/transcribed and *not* considered good practice; `day-007.md`
(written independently) was the actual example that worked. Landed on a
compromise for `journal/day-008.md` and future days: mentor asks a fixed
set of short content questions (what happened / what confused you / what
mistake or uncertainty / one-sentence concept takeaway), Juan answers each
in one line from his own recall, mentor only formats those answers into
the existing template (headers/bullets) — no content or phrasing supplied
by the mentor. Use this pattern for future daily journal entries unless
Juan raises it again.

Assessment:
- Commit message convention (summary line length, imperative mood): Practiced
- PR workflow (create, review diff, choose merge strategy, merge): Practiced
- Squash-merge mechanics and its effect on local/remote divergence: Introduced,
  reinforced through a real (unplanned) hands-on recovery — needs another
  rep before "independently demonstrated"
- `git reset --hard`: Introduced (one guided, verified-safe instance only;
  revisit properly under Day 009's "recovery from mistakes" topic)
- Diverged vs. conflict distinction: Practiced, held up under a second
  spaced-review pass after one repeated wrong answer

Journal:
- journal/day-008.md

Handbook:
- handbook/git.md ("What's a pull request?", "Commit message convention",
  "Merge Strategies")

Repo state at end of session: `main` and `origin/main` synced at `8676b70`,
only `main` remains locally and on GitHub, working tree clean.

---

## Day 009 - Recovery from common Git mistakes (IN PROGRESS, paused mid-session)

Status: In progress — not yet complete. Resume from "Where we left off" below.
Do not restart from scratch; do not skip the pending independent challenge.

Spaced-review check-in (done, before new material):
- Why squash-merge caused local/remote divergence on Day 008: correct
  immediately ("no shared history").
- Why `git branch -d` didn't refuse to delete the squash-merged branch:
  did not remember at first (flagged honestly instead of guessing) — walked
  back to first principles ("own upstream?") and got there correctly:
  `-d` checks the branch's own tracked upstream/HEAD, never `main` directly.

Documentation-integrity note (4th occurrence, same pattern as Days
006/007/008): asked Juan to add a `handbook/git.md` note explaining why
`-d` didn't warn. First attempt was near-verbatim copy of the mentor's
wording; rejected. Second attempt changed one word; rejected again. Third
attempt, after being told explicitly to say it out loud in chat *before*
touching the file (he skipped that step and edited directly anyway), used
genuinely different phrasing ("reachable from its tracked upstream") and
was accepted. Process change agreed for future sessions: for concepts
prone to this, Juan should state his explanation in chat first, before the
mentor gives its version, so there's nothing to copy from yet.

Covered so far (all hands-on, on a real sandbox branch `day-009-reset-practice`,
created off `main` at `18be9e7`):
- `git reset --soft/--mixed/--hard <commit>` — table taught (effect on
  branch pointer / index / working tree), then each mode actually run and
  verified via `git status` + `git log`, not just explained.
- Real unplanned mistake used as a live `--mixed` demo (better than a
  staged one): Juan ran `git add .` instead of `git add reset-practice.md`
  while committing, which swept in an unrelated pending `handbook/git.md`
  edit into the same commit. Self-diagnosed the cause correctly ("Oh shit
  I ran git add ."). Fixed live with `git reset --mixed HEAD~1` (predicted
  the outcome correctly first), then re-split into two separate commits.
- Follow-on real mistake: the split-out `handbook/git.md` commit
  (`efa1341`, "add why git branch -d didn't warn me") existed only on the
  throwaway sandbox branch, not on `main`. Juan correctly predicted the
  consequence (commit would be lost if the branch were later deleted).
  Fixed by introducing `git cherry-pick` (not on today's official topic
  list, but the right tool for "move one specific commit to another
  branch" — flagged as introduced opportunistically, like rebase was on
  Day 008/009 prep notes). Cherry-picked cleanly onto `main` as `f2a1cf6`,
  pushed, verified `main`/`origin/main` synced.
- `--hard` demonstrated deliberately: committed "line two", correctly
  predicted it would be unrecoverable via `--soft`/`--mixed`-style undo but
  recoverable via reflog, ran `git reset --hard HEAD~1`, confirmed content
  gone from the file and commit gone from `git log`.
- `git reflog`: read real reflog output (60+ entries, full project
  history), correctly identified which of two duplicate "add line two..."
  entries was the right one to recover (the most recent, right before the
  most recent reset — not the older one from the `--soft` demo). Recovered
  with `git reset --hard <hash>`, verified file content and log.
- `git revert`: conceptual question first (why is `reset --hard` dangerous
  on a shared/pushed branch, why isn't `revert`) — first answer conflated
  "deletes teammate's commits" with the real mechanism; corrected to the
  precise version (reset requires a force-push to publish, which rewrites
  shared history teammates already have; revert adds a new forward commit,
  nothing rewritten). Then ran `git revert ce5ed34` for real, confirmed the
  original commit stays in `git log` (nothing erased) and a new revert
  commit sits on top.
- `git commit --amend`: conceptual question first (same shared-history
  danger as reset, because amend replaces the commit with a new hash) —
  answered correctly unprompted. Then ran it for real (added "line three",
  amended into the revert commit), confirmed hash changed
  (`d012b10` → `e2b6cfd`) but position/parent in history stayed the same.
- Documentation check: read `git reset --help`'s description of
  `--soft`/`--mixed`/`--hard` directly, compared against the taught table.
  Confirmed alignment; also caught a real nuance the table didn't cover —
  `--hard` can delete *untracked* files/directories if they're "in the way
  of writing any tracked files," not just reset tracked-file changes.

Where we left off (independent challenge, NOT yet completed):
Scenario given: current HEAD (`e2b6cfd`, the amended revert commit,
unpushed) contains `reset-practice.md` with "line one" and "line three".
Juan was asked to remove "line three" from that commit using whichever
tool from today fits, and to state which tool and why *before* running
anything. He had not yet answered when the session paused. Resume by
re-presenting this exact scenario (don't skip it or replace it with a new
one) — natural fits are `--amend` again (edit file, `commit --amend`) or
`reset --soft`/`--mixed` + edit + recommit; either is defensible, the
point is he chooses and justifies it himself.

Still pending after the challenge (do not skip):
- Teach-back: have him explain reset (soft/mixed/hard) vs. revert vs.
  amend in his own words, English, unprompted.
- Handbook notes: `handbook/git.md` needs entries for `git reset`
  (three modes), `git reflog`, `git revert`, and `git commit --amend`,
  written by Juan (watch for the documentation-integrity pattern flagged
  above — have him explain verbally before writing, given today's
  4th-occurrence catch).
- Journal entry for Day 009 (short Q&A format from Day 008, mentor
  formats only).
- Sandbox cleanup: `day-009-reset-practice` branch still exists locally
  only (never pushed), currently sitting on `e2b6cfd`. Decide with Juan
  whether to delete it after the challenge/handbook notes are done, or
  keep it briefly for the teach-back.
- Assessment classification for reset/revert/reflog/amend (none assigned
  yet — session paused before this point).
- Rebase-and-merge still flagged unpracticed from Day 008 — still
  opportunistic, not urgent.

Repo state at pause point:
- `main`/`origin/main` synced at `f2a1cf6` ("add why git branch -d didn't
  warn me" — the cherry-picked commit).
- `day-009-reset-practice` (local only, not pushed) at `e2b6cfd`, working
  tree clean.
- `git cherry-pick` was introduced today though not on the original Day 009
  topic list — note for whoever resumes this session.
- Continue the new journal-writing process from Day 008 (short Q&A,
  mentor formats only) for the Day 009 entry, once we get there.
