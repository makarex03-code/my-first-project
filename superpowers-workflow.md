# Builder's Workflow with Superpowers

The five-phase workflow that every build follows. Use slash commands to invoke each phase explicitly.

---

## Superpowers Slash Commands — Quick Reference

| Command | Phase | What It Does |
|---|---|---|
| `/superpowers:brainstorming` | Brainstorm | Explores your idea, asks questions, produces a structured spec |
| `/superpowers:writing-plans` | Plan | Creates a phased implementation plan from your spec |
| `/superpowers:using-git-worktrees` | Execute | Sets up an isolated workspace so your main code stays safe |
| `/superpowers:executing-plans` | Execute | Executes the plan task by task with subagents |
| `/superpowers:systematic-debugging` | Test/Fix | Four-phase root cause analysis when something breaks |
| `/superpowers:requesting-code-review` | Test | Gets a thorough code review before shipping |
| `/superpowers:verification-before-completion` | Test | Verifies everything actually works before you claim done |
| `/superpowers:finishing-a-development-branch` | Ship | Guides merge, PR, or cleanup when work is complete |

> **Why use slash commands instead of just describing what you want?**
> Slash commands give you explicit control over which skill activates. Instead of hoping Claude Code picks the right one, you tell it exactly what to do. This is more reliable, especially when you're learning.

---

## The Five Phases

### 1. BRAINSTORM
**Slash command:** `/superpowers:brainstorming` → Then describe what you want to build.

- **Your job:** Describe your idea and answer Superpowers' clarifying questions.
- **Superpowers' job:** Digs into who it's for, what it does, scope, design direction, data needs. Produces a structured spec.
- **Done when:** You have a structured spec that matches your vision.

---

### 2. PLAN
**Slash command:** `/superpowers:writing-plans`

- **Your job:** Review and approve the plan.
- **Superpowers' job:** Writes a phased implementation plan with small, specific tasks. Saves it to `plan.md`.

**Review the plan:**
- Do the phases make sense?
- Is anything missing?
- Is anything too big? (Ask to break it down further)

- **Done when:** You've approved the plan.

---

### 3. EXECUTE
**Slash commands:**
1. `/superpowers:using-git-worktrees` — Sets up an isolated workspace first (recommended).
2. `/superpowers:executing-plans` — Executes the plan task by task.

- **Your job:** Watch, give feedback, and verify between phases.
- **Superpowers' job:** Builds each phase using TDD, code review, and subagents.

**What Superpowers does automatically:**
- Breaks work into small tasks and dispatches subagents
- TDD — Writes a test first, then writes code to pass it
- Code review — Reviews work between steps
- Git worktrees — Builds in an isolated branch (your main code stays safe)

**Give feedback between phases:**
- "The layout should be different — [describe]"
- "That feature isn't working correctly — [describe expected vs actual]"
- "Skip this phase, I don't need it"

- **Done when:** All phases are built and passing tests.

---

### 4. TEST
**Slash commands:**
- `/superpowers:systematic-debugging` — Use when something is broken — finds root cause before fixing.
- `/superpowers:requesting-code-review` — Use to get a thorough review of the whole project.
- `/superpowers:verification-before-completion` — Use to verify everything works before you ship.

- **Your job:** Use the app like a real user. Try to break it.
- **Superpowers' job:** Runs all tests, code review, verification checks.

**Manual testing checklist:**
- Does the happy path work?
- What happens with empty / weird / extreme inputs?
- Does it work on mobile?
- Is the design consistent?

If something's broken, use:
```
/superpowers:systematic-debugging [Describe what's wrong]. The expected behavior is [what should happen].
```

- **Done when:** Everything works, code review is clean, and verification passes.

---

### 5. SHIP
**Slash command:** `/superpowers:finishing-adevelopment-branch`

- **Your job:** Choose how to integrate (merge, PR, or cleanup).
- **Superpowers' job:** Verifies tests pass, presents options, handles the chosen workflow.

**Then deploy:**
```
/superpowers:finishing-a-development-branch Deploy this project to Vercel.
```

- **Done when:** Your app has a live URL and you've shared it.

---

## The Full Flow — Command by Command

```
Step 1: /superpowers:brainstorming               → Describe your idea
Step 2: /superpowers:writing-plans               → Review the plan
Step 3: /superpowers:using-git-worktrees         → Set up isolated workspace
Step 4: /superpowers:executing-plans             → Build it
Step 5: /superpowers:requesting-code-review          → Review the work
Step 6: /superpowers:verification-before-completion  → Verify it works
Step 7: /superpowers:finishing-a-development-branch  → Merge and ship
```

---

## Session Management

| When | What to do |
|---|---|
| Start of every session | Read the `CLAUDE.md` and `plan.md` files. Pick up where we left off. |
| When context is getting long | `/compact` |
| Before ending a session | Make sure `plan.md` is updated with current progress. |

---

## Key Files

| File | What It Is | Who Creates It |
|---|---|---|
| `CLAUDE.md` | Project memory — conventions, tech stack, preferences | Created with `/init`, updated as needed |
| `plan.md` | Implementation plan — what's done, what's next | Superpowers creates and updates it |
