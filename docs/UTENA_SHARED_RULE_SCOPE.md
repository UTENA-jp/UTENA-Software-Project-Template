# UTENA Shared Rule Scope

## Absolute scope rule

UTENA-wide shared rules may contain **development principles only**. They must never carry project-specific state from one repository into another.

### Shared across all UTENA apps
- No duplicate instruction execution
- No regression
- No destructive data handling
- Explicit PASS / FAIL criteria
- Concrete numerical targets where applicable
- User confirmation required before declaring completion
- Preserve previously working behavior
- Do not silently weaken tests
- Do not re-run an already completed identical instruction unless Takashi explicitly requests a rerun

### NEVER inherit from another repository
The following are repository-local and must never be copied, inferred, inherited, or used as stop/go conditions for another app:
- PROJECT_STATE.md
- STATUS.md
- ROADMAP
- checkpoint
- current task
- branch / worktree state
- acceptance state
- device state
- test counts
- milestone / phase numbers
- feature names
- data model / schema state
- stop conditions
- user-verification state
- any project-specific instructions

## Required repository isolation
Before acting, the agent must identify the current repository and use only that repository's local state documents and current user instruction for project-specific decisions.

If information from another repository appears in context, it is reference-only and MUST NOT control the current repository.

If a shared-rule document contains a project-specific example, the example is illustrative only and MUST NOT be treated as current state or instruction.

## Cross-project contamination = FAIL
If the agent uses another app's PROJECT_STATE / STATUS / ROADMAP / checkpoint / current task as a reason to stop, continue, implement, test, or declare completion, that is a process failure. Stop state-changing work, discard that cross-project assumption, re-read the current repository's own state, and resume from the current app's actual task.

**Principle:** Share development rules. Never share project state.