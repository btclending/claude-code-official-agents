---
description: "Review a skill for quality, triggering effectiveness, and best practices"
argument-hint: "<skill-path>"
allowed-tools: ["Read", "Glob", "Grep", "Task"]
---

# Review Skill Quality

Review a skill for quality, triggering effectiveness, and adherence to best practices.

**Skill Path:** "$ARGUMENTS"

## What This Command Does

Uses the `skill-reviewer` agent to evaluate:

1. **Structure Validation**
   - Frontmatter format (YAML between `---`)
   - Required fields: `name`, `description`
   - Body content exists and is substantial

2. **Description Quality** (Most Critical)
   - **Trigger Phrases**: Specific phrases users would say
   - **Third Person**: Uses "This skill should be used when..."
   - **Specificity**: Concrete scenarios, not vague
   - **Length**: 50-500 characters
   - **Example Triggers**: Lists specific queries

3. **Content Quality**
   - **Word Count**: 1,000-3,000 words ideal
   - **Writing Style**: Imperative/infinitive form
   - **Organization**: Clear sections, logical flow
   - **Specificity**: Concrete guidance

4. **Progressive Disclosure**
   - Core SKILL.md has essential info only
   - `references/` for detailed docs
   - `examples/` for working code
   - `scripts/` for utilities
   - Clear pointers to resources

5. **Supporting Files**
   - Quality and relevance of references
   - Completeness of examples
   - Documentation of scripts

## How to Use

```
/plugin-dev:review-skill skills/pdf-processing/SKILL.md
/plugin-dev:review-skill plugins/my-plugin/skills/api-design/
```

## Output Format

```
## Skill Review: pdf-processing

### Summary
Good skill with room for improvement in description.

### Description Analysis
**Current:** "Handles PDF files"

**Issues:**
- Too vague, no trigger phrases
- Missing example queries

**Recommendations:**
- Add: "process PDF", "extract text from PDF"
- Suggested: "This skill handles PDF file processing including..."

### Content Quality
- Word count: 2,450 (good)
- Writing style: Mixed (needs consistency)
- Organization: Clear sections

### Progressive Disclosure
- SKILL.md: 2,450 words
- references/: 2 files (good)
- examples/: 3 files (good)

### Overall Rating
Needs Improvement

### Priority Recommendations
1. Improve description with trigger phrases
2. Make writing style consistent
3. Add more example queries
```

## When to Use

- After creating a new skill
- After modifying skill content
- Before publishing a skill
- When skill isn't triggering properly
