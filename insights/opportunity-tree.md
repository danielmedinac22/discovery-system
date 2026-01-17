# Opportunity Solution Tree

## Business Outcome
[This will be populated from context/business-outcome.md]

Example: "Increase activation rate from 42% to 55% in Q1 2026"

---

## Opportunities

### Opportunity 1: [Name of Opportunity]

**Description:**
[Clear description of the user problem or need]

**Evidence:**
- User A (YYYY-MM-DD): "[exact quote]"
- User B (YYYY-MM-DD): "[exact quote]"
- User C (YYYY-MM-DD): "[exact quote]"

**Frequency:** X/Y users mentioned this
**Pain Level:** High / Medium / Low
**Connection to Outcome:** [How solving this impacts the current outcome]

**Solutions to Explore:**
1. [Solution idea 1]
   - Effort: Low / Medium / High
   - Impact: Low / Medium / High
   - Description: [What this solution does]

2. [Solution idea 2]
   - Effort: Low / Medium / High
   - Impact: Low / Medium / High
   - Description: [What this solution does]

3. [Solution idea 3]
   - Effort: Low / Medium / High
   - Impact: Low / Medium / High
   - Description: [What this solution does]

**Recommendation:** [Which solution to test first and why]

**Status:** Not Started / Testing / Validated / Deprioritized

---

### Opportunity 2: [Name of Opportunity]

[Same structure as above]

---

### Opportunity 3: [Name of Opportunity]

[Same structure as above]

---

## Insights Log

This section tracks when opportunities were added or updated.

- YYYY-MM-DD: Added Opportunity 1 based on [User A] + [User B] interviews
- YYYY-MM-DD: Updated Opportunity 1 with evidence from [User C] (now 3/3 recent users)
- YYYY-MM-DD: Added Opportunity 2 based on [User D] interview (single mention, needs validation)
- YYYY-MM-DD: Promoted Opportunity 2 to high priority (now mentioned by 4/5 users)

---

## How To Use This Tree

1. **After each interview:** Ask Claude to analyze the transcript and update this tree
2. **Weekly review:** Look at which opportunities have the most evidence
3. **Prioritization:** Focus on opportunities with:
   - High frequency (mentioned by multiple users)
   - Strong connection to current outcome
   - High pain level (emotional language, workarounds)
4. **Testing:** Pick one solution per opportunity to test first
5. **Iteration:** Update status as you test and learn

**Example command for Claude:**
```
"Analyze transcripts/2026-01-15-jane-doe.md and update this opportunity tree.
Look for new opportunities or evidence supporting existing opportunities."
```

---

## Template for Adding New Opportunities

When Claude identifies a new opportunity, it will use this format:

```markdown
### Opportunity X: [Clear, User-Focused Name]

**Description:**
[1-2 sentences describing the problem from the user's perspective]

**Evidence:**
- User Name (date): "[quote showing pain point]"

**Frequency:** 1/Y users (needs more evidence)
**Pain Level:** [High/Medium/Low based on language and context]
**Connection to Outcome:** [Specific explanation of how this impacts current metric]

**Solutions to Explore:**
[Claude will suggest 3-5 initial solution ideas]

**Recommendation:** Need more evidence (only 1 user mention) - continue interviewing

**Status:** Not Started
```
