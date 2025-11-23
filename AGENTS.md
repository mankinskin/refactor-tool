# Agent Rules & Code Requirements

> **⚠️ MANDATORY: READ THIS FILE FIRST** before any code changes in this workspace.

Code requirements and development rules for the refactor-tool project.

> **AGENT RESPONSIBILITY:** Keep this file current. Update immediately when requirements change.
>
> **Update triggers:** Project structure changes, new test patterns, modified debugging workflows, requirement changes.

> **🔍 CONFUSED? CHECK `agents/guides/INDEX.md` FIRST** - Search by tags before asking questions or researching.

## 📚 Documentation Maintenance

**⚠️ CRITICAL: Update docs when changing code!**

### Before Work:
1. `CHEAT_SHEET.md` - API patterns (TODO: create when needed)
2. Module-specific guides in `agents/guides/` - How-tos and troubleshooting
3. Existing documentation files (FEATURES.md, MODULES.md, ARCHITECTURE_ANALYSIS.md)

### After Changes:
| Change Type | Update File |
|------------|-------------|
| API/types/patterns | `CHEAT_SHEET.md` (TODO: create) |
| Architecture/modules | Relevant docs in root + `agents/guides/` |
| Unclear behavior/gaps | `QUESTIONS_FOR_AUTHOR.md` (TODO: create) |
| Test structure/workflows/commands | `AGENTS.md` (this file) |

## Problem-Solving Approach

### Complex Tasks: Plan First, Execute Later

**For multi-file refactors, large features, or architectural changes:**

1. **Planning session (research-focused):**
   - Create `agents/plans/PLAN_<task_name>.md` (use template in `agents/plans/`)
   - Include: Objective, Context, Analysis, Execution steps, Risks, Validation
   - Gather ALL context before planning
   - Ask user to clarify unknowns
   - Don't implement yet - just plan

2. **Execution session (fresh context):**
   - Load plan from `agents/plans/`
   - Execute steps sequentially
   - Verify each step before proceeding
   - Update plan if deviations needed
   - Mark completed items
   - When done: Create summary in `agents/implemented/`, update INDEX.md, keep or archive plan

**Benefits:**
- Fresh context = more tokens for code
- Complete picture before starting
- Parallel execution possible (multiple agents)
- Recoverable from failures
- User can review plan before execution

**When to use:** >5 files affected, >100 lines changed, or unclear scope

**When to skip:** Simple fixes, single-file changes, clear implementation path

### When Confused: Research → Document (or Ask)

1. **Don't guess!** Check `agents/guides/INDEX.md` by tags first
2. **Quick research:** Read source, check docs, scan tests (10-15 min max)
3. **Still unclear? → Ask user** rather than deep rabbit holes
4. **After user clarifies:** Document in `agents/guides/<TOPIC>_GUIDE.md`:
   - Problem description + root cause
   - Correct/incorrect examples
   - Common mistakes + fixes
   - Related files + migration checklist
5. **Update index:** Add to `agents/guides/INDEX.md` (or note "TODO" if urgent)

**When to defer to user:**
- Research taking >15 minutes without clarity
- Multiple plausible interpretations
- Contradictory expectations or evidence
- Domain-specific knowledge needed
- Architecture decisions required

### Context-First Strategy

**Gather context before coding.**

| Context Level | Includes |
|--------------|----------|
| ❌ Minimal | Error only |
| ⚠️ Basic | Error + code |
| ✓ Good | + tests/expectations |
| ✓✓ Better | + data flow |
| ✓✓✓ Best | + architecture |

**Context sources:** `ls`/`find` → docs → tests → `git log -p` → ask user

**Red flags:** Repeated failures, unclear values, uncertain ownership, many unknown refs

## Project Structure

AI-powered Rust refactoring tool with CLI interface for code transformation and analysis.

**Core modules:**
- `src/ai/` - AI provider integrations (OpenAI, etc.)
- `src/analysis/` - Code analysis, imports, exports, duplication detection
- `src/cli/` - Command-line interface and argument parsing
- `src/core/` - Core refactoring engine and AST management
- `src/io/` - File I/O and workspace management
- `src/syntax/` - Rust syntax parsing, transformation, and navigation
- `src/server/` - Optional embedded LLM server (Candle)

**Architecture:** Analysis → AST transformation → Code generation → Validation

**See also:** MODULES.md, FEATURES.md, ARCHITECTURE_ANALYSIS.md for detailed documentation

## Documentation Resources

**Priority order:**
1. **`AGENTS.md`** - This file (START HERE)
2. **`agents/guides/INDEX.md`** - How-to guides by topic (TODO: populate)
3. `FEATURES.md` - Feature descriptions and capabilities
4. `MODULES.md` - Module structure and responsibilities
5. `ARCHITECTURE_ANALYSIS.md` - Architecture decisions and patterns
6. `tests/TESTING_FRAMEWORK.md` - Test organization and patterns
7. `agents/bug-reports/INDEX.md` - Known issues (TODO: create as needed)
8. `cargo doc --open` - Generated API documentation

## Testing & Debugging

### Test Structure
- Unit tests: In-module tests for individual functions
- Integration tests: `tests/` directory with fixture workspaces
- Test fixtures: `tests/fixtures/` - Various workspace configurations

### Test Commands
```bash
# Run all tests
cargo test

# Run specific test
cargo test <test_name> -- --nocapture

# Run tests for specific module
cargo test --lib <module_path>

# Run integration tests
cargo test --test <test_file>
```

### Debug Workflow
1. Identify failing test or behavior
2. Check existing test fixtures in `tests/fixtures/`
3. Run with `-- --nocapture` to see output
4. Use `dbg!()` or `eprintln!()` for debugging
5. Check `tests/common/` for test utilities and assertions

## Bug Reports

Check `agents/bug-reports/INDEX.md` before investigating (TODO: create as needed).

**Format:** `agents/bug-reports/BUG_<component>_<desc>.md` with: Summary, Root Cause, Evidence, Fix Options, Related Files

**After creating:** Add entry to `agents/bug-reports/INDEX.md` with tags and summary

**After fixing:** Update guides in `agents/guides/`, archive/update bug report in INDEX.md, document pattern

## Agentic Workflow Organization

**Use `agents/` directory to keep repository organized. See `agents/README.md` for complete guide.**

**Directory structure:**
- `agents/guides/` - How-to guides and troubleshooting (commit these)
- `agents/plans/` - Task plans before execution (commit active plans)
- `agents/implemented/` - Completed feature documentation (commit these)
- `agents/bug-reports/` - Known issues and analyses (commit these)
- `agents/analysis/` - Architecture and design analyses (commit these)
- `agents/tmp/` - Temporary scratch files (never commit)

**Quick decision tree:**
- Confused? → Check `agents/guides/INDEX.md` → Research 10-15min → Still unclear? Ask user → Document in `agents/guides/` + **update INDEX.md**
- Large task (>5 files)? → Create plan in `agents/plans/` → Execute later → Summary in `agents/implemented/` + **update INDEX.md**
- Found bug? → Document in `agents/bug-reports/` + **update INDEX.md** → After fix, update `agents/guides/`
- Feature done? → Write summary in `agents/implemented/` + **update INDEX.md**

**Move findings from tmp/ to:** CHEAT_SHEET.md (patterns) | `agents/guides/` (how-tos) | Relevant root docs | QUESTIONS_FOR_AUTHOR.md (questions)

**Full documentation:** `agents/README.md` - Master index with when-to-use guide for each directory

## Key Documentation Files

- **Root:** README.md (TODO: create), FEATURES.md, MODULES.md, ARCHITECTURE_ANALYSIS.md
- **Testing:** tests/TESTING_FRAMEWORK.md, tests/fixtures/README.md
- **Development:** REFACTORING_STEPS.md, CURRENT_REFACTORING_ANALYSIS.md
- **Features:** CANDLE_SERVER.md, EMBEDDED_LLM_PLAN.md, SUBCOMMANDS.md
