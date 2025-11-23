# Bug Reports Index

> **Purpose:** Track known issues with detailed analysis and status.

## 🔴 Active Issues

*No active bug reports - create reports as issues are discovered.*

---

## ✅ Resolved Issues

*No resolved bugs yet - move fixed bugs here with resolution details.*

---

## Template for New Bug Reports

Create `BUG_<component>_<short_desc>.md` with:

```markdown
# Bug: [Title]

**Component:** [e.g., parser, imports, CLI]  
**Severity:** Critical / High / Medium / Low  
**Status:** Active / In Progress / Resolved  
**Discovered:** YYYY-MM-DD

## Summary
Brief description of the bug.

## Root Cause
Technical explanation of why it happens.

## Evidence
- Code locations
- Test failures
- Error messages
- Reproduction steps

## Fix Options
1. **Option A:** Description + trade-offs
2. **Option B:** Description + trade-offs

## Related Files
- `src/module/file.rs`
- `tests/test_file.rs`

## Resolution
*(Add after fix):*
- Fixed in commit: [hash]
- Solution chosen: [which option]
- Related guide: [link to guide created]
```

---

## Index Entry Format

```markdown
### [BUG_component_desc](BUG_component_desc.md)
**Status:** 🔴 Active / 🔄 In Progress / ✅ Resolved  
**Severity:** Critical / High / Medium / Low  
**Summary:** One-line description  
**Assigned:** (optional)
```

---

## Guidelines

1. Create bug report immediately upon discovery
2. Include reproduction steps and evidence
3. Update status as work progresses
4. After fix: Update guides/ with pattern learned
5. Move to "Resolved" section with resolution details
