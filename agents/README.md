# Agents Directory Structure

This directory organizes agentic workflows for the refactor-tool project. All AI-assisted work should be documented here to maintain clarity and enable collaboration.

## 📁 Directory Overview

### `guides/` - How-To Guides & Troubleshooting
**Purpose:** Reusable solutions to common problems and patterns  
**Commit:** ✅ Yes - valuable knowledge base  
**When to use:**
- Solved a confusing problem
- Found a non-obvious pattern
- Common mistakes to avoid
- Step-by-step procedures

**Format:** `<TOPIC>_GUIDE.md` with clear examples and gotchas  
**Index:** Maintain `guides/INDEX.md` with tags and summaries

### `plans/` - Task Plans Before Execution
**Purpose:** Planning complex multi-step tasks before implementation  
**Commit:** ✅ Active plans / ⏸️ Archive completed  
**When to use:**
- >5 files affected
- >100 lines changed
- Unclear scope requiring research
- Multi-session work

**Format:** Use `PLAN_TEMPLATE.md` template  
**Workflow:** Plan → Review → Execute → Document in `implemented/`

### `implemented/` - Completed Feature Documentation
**Purpose:** Record what was built and how it works  
**Commit:** ✅ Yes - permanent record  
**When to use:**
- After completing a major feature
- After finishing a plan
- Significant refactoring complete

**Format:** `<FEATURE_NAME>.md` with summary, changes, testing, notes  
**Index:** Maintain `implemented/INDEX.md` with chronological entries

### `bug-reports/` - Known Issues & Analyses
**Purpose:** Track bugs with detailed analysis  
**Commit:** ✅ Yes - team awareness  
**When to use:**
- Discovered a bug
- Non-trivial issue needing investigation
- Workarounds documented

**Format:** `BUG_<component>_<description>.md` with root cause analysis  
**Index:** Maintain `bug-reports/INDEX.md` with status and priority

### `analysis/` - Architecture & Design Analysis
**Purpose:** Deep dives into design decisions and architecture  
**Commit:** ✅ Yes - valuable insights  
**When to use:**
- Analyzing architectural decisions
- Comparing implementation approaches
- Performance or design trade-offs
- System-wide impact analysis

**Format:** `<TOPIC>_ANALYSIS.md` with thorough investigation  
**Index:** Maintain `analysis/INDEX.md` with summaries

### `tmp/` - Temporary Scratch Work
**Purpose:** Temporary notes, experiments, incomplete analysis  
**Commit:** ❌ NEVER - add to .gitignore  
**When to use:**
- Active investigation
- Incomplete research
- Debugging notes
- Quick experiments

**Cleanup:** Move valuable findings to appropriate permanent directory

## 🔄 Workflow Patterns

### Pattern 1: Confused About Something
```
1. Check guides/INDEX.md by tags
2. Quick research (10-15 min max)
3. Still unclear? → Ask user
4. User clarifies → Document in guides/
5. Update guides/INDEX.md
```

### Pattern 2: Large Feature/Refactor
```
1. Create plans/PLAN_<name>.md (use template)
2. Research and gather context
3. Write complete plan
4. User reviews plan
5. Execute in new session
6. Document in implemented/<FEATURE>.md
7. Update implemented/INDEX.md
8. Archive or keep plan
```

### Pattern 3: Bug Discovery
```
1. Reproduce and investigate
2. Document in bug-reports/BUG_<name>.md
3. Update bug-reports/INDEX.md
4. Fix bug (or mark as known issue)
5. After fix: Update guides/ with pattern
6. Mark bug as resolved in INDEX.md
```

### Pattern 4: Architecture Analysis
```
1. Deep dive into design question
2. Document findings in analysis/<TOPIC>_ANALYSIS.md
3. Include trade-offs, alternatives, recommendations
4. Update analysis/INDEX.md
5. Reference in relevant guides/
```

## 📝 Index Files (Important!)

Each major directory should have an `INDEX.md` file:

**guides/INDEX.md:**
```markdown
# Guides Index

## By Topic
- **Import/Export Processing** - [IMPORT_EXPORT_GUIDE.md](IMPORT_EXPORT_GUIDE.md)
- **AST Transformation** - [AST_TRANSFORM_GUIDE.md](AST_TRANSFORM_GUIDE.md)

## By Tags
#imports #exports #syntax
#ast #transformation #refactoring
```

**implemented/INDEX.md:**
```markdown
# Implemented Features

## 2025-11
- [Feature Name](FEATURE_NAME.md) - Brief description
```

**bug-reports/INDEX.md:**
```markdown
# Bug Reports

## Active
- [BUG_parser_handling](BUG_parser_handling.md) - Parser fails on...

## Resolved
- ~~[BUG_import_resolution](BUG_import_resolution.md)~~ - Fixed in commit abc123
```

**analysis/INDEX.md:**
```markdown
# Architecture Analysis

- [Import Strategy Comparison](IMPORT_STRATEGY_ANALYSIS.md)
- [AST vs String-based Refactoring](REFACTORING_APPROACH_ANALYSIS.md)
```

## 🎯 Best Practices

1. **Always update INDEX.md** when creating new documents
2. **Use clear, descriptive filenames** with prefixes (BUG_, PLAN_, etc.)
3. **Cross-reference related documents** using relative links
4. **Keep tmp/ clean** - move valuable content to permanent locations
5. **Add tags** to guides for easy searching
6. **Date entries** in implemented/ and bug-reports/
7. **Update AGENTS.md** when workflow patterns change

## 🚫 What NOT to Do

- Don't commit tmp/ files (should be .gitignored)
- Don't create duplicate guides - update existing ones
- Don't skip INDEX.md updates - they're critical for navigation
- Don't write plans without using the template
- Don't leave TODOs in completed documentation

## 📚 Related Files

- **AGENTS.md** - Main agent rules and requirements (read first!)
- **CHEAT_SHEET.md** - Quick API reference (TODO: create when needed)
- **QUESTIONS_FOR_AUTHOR.md** - Questions for maintainer (TODO: create)
