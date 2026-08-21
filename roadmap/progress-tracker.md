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

## Day 009 - Recovery from common Git mistakes

Status: Completed (resumed across two sessions — see "Session resumed" below for
the second half).

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

### Session resumed (real gap of several days between the pause above and this)

Juan opened the session not remembering where things had been left — flagged
honestly rather than guessing, handled by a light spaced-review pass (reset
modes, why `--hard` is dangerous on shared/pushed branches, what `revert`
actually does) before returning to the paused independent challenge. Retrieval
was rusty on two specific points (both previously-flagged nuances: `--mixed`
still leaves changes in the working tree just unstaged; the shared-branch
danger of `--hard` is specifically about needing a force-push, not "not
verifying anything") — corrected in place, held up under a follow-up.

Independent challenge (resumed, completed): remove "line three" from
`reset-practice.md` on the amended revert commit `e2b6cfd`. Juan chose
`git commit --amend` and, after one scaffolded nudge ("what would `reset
--soft` still leave you to do afterward?"), correctly articulated *why*
amend fits better than `reset --soft` here (amend folds edit+recommit into
one step; both were equally safe here since the commit was unpushed).
Executed for real: edited the file in VS Code, `git add`, `git commit
--amend`, verified via `git log --oneline -3` that the hash changed
(`e2b6cfd` → `5d478ef`) while position/parent in history stayed the same.

Teach-back (reset/revert/amend): unprompted, correct, and notably solid —
correctly distinguished `--soft` (staged, useful for combining local
commits) vs. `--mixed` (unstaged but still in working tree, useful for
recommitting differently) vs. `--hard` (discarded from both, only safe when
unwanted and nobody else is on the branch); correctly tied `revert`/`amend`
to private-vs-shared-history safety. Landed on his own rule of thumb:
"reset/amend for cleaning up private history; revert for safely undoing
shared history."

Documentation-integrity catch — **5th occurrence**, same pattern as Days
006/007/008/009 (first half): asked for a `reflog` teach-back next; the
answer was fluent, fully punctuated, used phrases like "Git's local diary"
and "signpost" — a sharp register shift from every other answer in the
session (which were lowercase, typo'd, clearly live-typed). Flagged
directly by name-checking the register difference rather than the content;
Juan admitted immediately ("o read it online") without being pushed
further. Given this is now the 5th time, flagged in this tracker as
worth a direct, explicit conversation next session about *why* it keeps
happening, rather than continuing to just re-flag it each time it recurs.

Reflog rebuilt from scratch, this time for real: rather than re-asking for
recall, had Juan run `git reflog -10` on the actual repo and read real
output cold. Walked through `HEAD@{N}` ordering (correctly identified `{0}`
as most recent) and a concrete live example in the output — three different
commit hashes (`5d478ef`, `e2b6cfd`, `9795833`) all logged against the same
"Revert ..." amend action. Juan correctly reasoned (with one nudge) that
`--amend` creates a new commit object and moves the branch pointer, and
that the old object isn't deleted, just unreferenced, until garbage
collection — which is the actual mechanism behind why `reflog` could
recover the "line two" commit after `--hard`. Final teach-back, entirely
his own words this time: reflog as "history of where HEAD has pointed,"
recovery working "because it was no longer on branch or HEAD pointing at
it, with Git history I was able to recover it" — correct and defensible.

Handbook updated (`handbook/git.md`, new `## Recovery from Common Git
Mistakes` section): entries for `git reset` (three modes), `git reflog`,
`git revert`, `git commit --amend`, written by Juan from his own
already-articulated explanations. One typo caught and fixed (`--ammend` →
`--amend`). Reflog entry read slightly more polished than his live chat
answer but was judged to be normal writing-vs-talking cleanup, not a repeat
of the copy-paste pattern — same content, tighter sentences.

Journal: `journal/day-009.md` written using the Day 008 process (short
Q&A, mentor formats only, no content supplied by mentor).

Sandbox cleanup: handbook edits had been made directly on
`day-009-reset-practice` (uncommitted) — Git correctly refused a branch
switch until Juan resolved it. Same pattern as the earlier `efa1341`
cherry-pick moment; Juan proposed the fix himself (commit on the sandbox
branch, cherry-pick to `main`) without being told. Committed as `c811b7d`,
cherry-picked onto `main` as `f55535c`, pushed. `day-009-reset-practice`
then force-deleted with `git branch -D` (not `-d` — Juan correctly
predicted `-d` would refuse since none of the sandbox commits were ever
merged; this was flagged as the legitimate use case for `-D`, contrasted
with the Day 008 case where `-d` wrongly *didn't* refuse). Branch was never
pushed, so no remote cleanup was needed. Confirmed via `git branch -a`:
only `main`/`origin/main` remain.

### Assessment (final, both halves of Day 009 combined)

- `git reset` (soft/mixed/hard): **Practiced** — correct table recall,
  correct nuance on `--mixed` (working tree vs. staging) after one
  correction, multiple real recoveries across both session halves.
- `git revert`: **Practiced** — correct reasoning reproduced independently
  twice, including the precise "no force-push needed" mechanism (not just
  "doesn't delete teammate's commits").
- `git commit --amend`: **Practiced**, trending toward independently
  demonstrated — chose it correctly and unprompted for the independent
  challenge, justified the choice himself after one scaffolded nudge,
  executed cleanly.
- `git reflog`: **Introduced/Practiced**, not higher yet — genuine
  understanding by the end, but required real scaffolding (rebuilding from
  live `git reflog` output) after an admitted copy-paste attempt. Revisit
  with a fresh, from-scratch recall next spaced-review pass before calling
  this independently demonstrated.
- `git cherry-pick`: **Practiced** — opportunistic tool (not originally on
  Day 009's plan), now used correctly and independently twice in one day.
- Documentation-integrity pattern (5th occurrence): flagged for a direct
  conversation next session, not just another inline catch-and-correct.

Repo state at end of session: `main`/`origin/main` synced at `f55535c`
("add reset, reflog, revert, amend notes"). No other local branches.
Working tree clean.

Journal:
- journal/day-009.md

Handbook:
- handbook/git.md ("Recovery from Common Git Mistakes")

Next class: **Day 010** — topic not yet chosen. Candidates flagged as
opportunistic-but-not-yet-covered: rebase-and-merge (flagged unpracticed
since Day 008/009), or move on to the next item in
`curriculum-phases.md`'s Phase 1 sequence. Also carry forward: a direct,
explicit conversation about the recurring documentation-integrity pattern
(5 occurrences now) before or alongside whatever technical topic comes
next.

---

## Day 010 - Rebase vs Merge

Status: Completed

Spaced-review check-in on Day 009 (done, before new material):
- Revert vs. `reset --hard` mechanism: first answer conflated the local
  effect of `--hard` (discards working tree/staging) with the actual reason
  it's dangerous on a *shared* branch. Corrected with Socratic scaffolding
  (direction of data flow, force-push, non-fast-forward refusal) rather than
  given the answer — ended with a fully correct, self-reconstructed
  explanation: shared history diverges, a normal `pull` gets refused because
  it can't fast-forward, and a teammate forcing their branch to match would
  lose any work built on the now-erased commits.
- `--mixed` vs `--hard` effect on working tree: correct immediately,
  including an unprompted correct note that `--mixed` is git reset's default
  mode.

Documentation-integrity conversation (direct, as flagged after the 5th
occurrence in Day 009): Juan named the real cause himself unprompted — "I
believe my own phrasing is not good enough." Mentor pushed back on that
framing (notes are for his own retention, not graded prose; a rougher
sentence he wrote himself is more valuable than a polished copied one).
Offered a hard verbal-first gate as a formal process change; Juan declined
the formal mechanism ("no need to say it out loud... I'll stop, no more
copy") and asked to self-regulate instead. Agreed compromise: no new
process imposed, but a 6th occurrence triggers the verbal-first gate for
real, no further negotiation. Today's actual handbook and journal writing
(see below) was checked against this and came back clean — content matched
his live chat register, no polish/formality shift detected.

Covered (hands-on, sandbox branch `day-010-rebase-practice`, deleted at
end of session):
- Concept taught: `rebase` vs `merge` — merge joins two histories with a
  merge commit (safe, nothing rewritten); rebase replays a branch's commits
  one-by-one onto a new base, giving each replayed commit a new hash
  (cleaner/linear history, but rewrites commits — same class of danger as
  `reset --hard`/`amend` on shared history).
- Clean rebase demonstrated first: created divergence (commit on sandbox
  branch, separate commit directly on `main` simulating a teammate), Juan
  correctly predicted before running it that his commit would get a new
  hash and sit after the `main`-side commit, then verified via
  `git log --graph --all` that the graph collapsed from two branches to a
  straight line.
- Conflict rebase demonstrated second (same line edited on both sides on
  purpose): correctly predicted a conflict would occur. First conflict came
  back as `(add/add)` rather than the usual "both modified" — Juan
  correctly reasoned why (the file never existed at the common ancestor;
  both sides created it independently in diverged history).
- Real mistake (not staged): first resolution attempt ran `git add` on the
  conflicted file *without* actually deleting the `<<<<<<<`/`=======`/
  `>>>>>>>` marker lines — Git doesn't validate marker removal, it just
  trusts whatever content is staged. This produced a second, nested
  conflict when the next queued commit (`687e3d0`) tried to apply on top of
  the still-marker-laden file. Juan self-diagnosed correctly when asked
  ("I just added the file without removing markers"). Recovered with
  `git rebase --abort` (correctly identified as the right tool, back to the
  exact pre-rebase diverged state, verified via `git log --graph --all`),
  then redid the rebase and resolved both conflicts properly.
- Second real mistake on the redo: after "cleanly" resolving, `cat` on the
  file revealed leftover ref-hash/commit-message text (e.g.
  `48ff4ef (add rebase-practice.md on feature branch)`) — Juan had deleted
  only the `>>>>>>>` marker symbol but left the trailing text that shared
  its line. Self-diagnosed again when asked. Fixed with `git commit
  --amend` (Juan chose the tool himself, correctly reasoning it was the
  unpushed tip commit on a private sandbox branch) — verified hash changed
  (`7c7462c` → `c4a418f`) and file content confirmed clean via `cat`.
- Documentation reading: `man git-rebase`, searched for and read the
  specific warning paragraph on rebasing published/shared history. Juan
  correctly tied it to the same underlying mechanism as the Day 009
  force-push discussion (rewriting history others already pulled).
- Full unprompted teach-back (merge vs. rebase, when each is safe/unsafe):
  accurate on every point, including a more precise formulation than a
  blanket rule — "NEVER rebase shared history unless it was explicitly
  coordinated," correctly allowing for team-coordinated exceptions rather
  than a flat never.
- Handbook (`handbook/git.md`, new `## Rebase Vs Merge` section) and
  journal (`journal/day-010.md`, same short-Q&A/mentor-formats-only process
  as Days 008/009) both written by Juan from his own already-articulated
  teach-back answers — checked directly against the live chat transcript,
  no copy-paste register shift found.
- Sandbox cleanup: `git branch -D day-010-rebase-practice` (Juan correctly
  chose `-D` over `-d`, reasoning the branch was never merged into `main`).
  Never pushed, so no remote cleanup needed. Verified via `git branch -a`:
  only `main`/`origin/main` remain.

### Assessment

- `git rebase` (basic replay onto an updated base): **Practiced** — correct
  prediction before running, correct interpretation of the resulting graph.
- Rebase conflict resolution (including recognizing `add/add` vs content
  conflicts): **Practiced** — genuine mistakes (marker text left in twice,
  in two different ways) worked through to a real fix rather than
  fixed-for-him; second mistake caught only because output was verified
  (`cat` the file) instead of trusting a "done"/clean-sounding claim.
- Merge vs. rebase conceptual distinction, including the shared-history
  danger: **Practiced, trending toward independently demonstrated** — full
  unprompted teach-back was accurate and included a nuance (coordinated
  exception) beyond what was taught directly.
- `git rebase --abort`: **Introduced/Practiced** — one real, correctly-used
  instance recovering from a botched conflict resolution.
- Documentation-integrity pattern: no new (6th) occurrence today; Juan
  self-regulated without the formal verbal-first gate. Revisit the
  hard-gate agreement immediately if it recurs.

Repo state at end of session: `main`/`origin/main` synced at `e9b0463`
("journal/day 10 rebase vs merge"). No other local or remote branches.
Working tree clean.

Journal:
- journal/day-010.md

Handbook:
- handbook/git.md ("Rebase Vs Merge")

Next class: **Day 011 — Phase 2, TypeScript and JavaScript fundamentals**
(confirmed with Juan at end of Day 010). Phase 1's readiness bar (explain
reset/revert/amend unprompted, diagnose diverged branches independently)
was already met as of Day 009, and rebase-and-merge — the last
opportunistic Phase 1 item — is now also practiced. See
`curriculum-phases.md`'s "Phase 2 — TypeScript and JavaScript fundamentals"
section for the learning/practice/produce targets. No unresolved blockers
carried forward from Day 010.
