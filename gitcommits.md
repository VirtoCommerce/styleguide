# Git commit message writing convention

## 1. Commit message structure
### Pattern:
`%type%: Commit message`

### Types:
- revert - used when some commits were reverted. Usually it is automatically filled by Git.
- feat - use it to tag some feature implementation.
- fix - use it to tag some bug fix.
- docs - use it to tag documentation improvements.
- style - use it to tag CSS changes.
- refactor - use it to tag some code style changes or significant code improvements.
- perf - use it to tag some performance improvements.
- test - use it to tag new or existing testing functionality.
- ci - use it to tag some ci/cd related commits.
- chore - use it to tag some background code-unrelated tasks.

### Examples
1. `feat: Add border to import label`
1. `fix: PR review fixes`
1. `ci: Update workflows`

## 2. Separate commit type and commit message subject line by a colon and blank

**Bad**
```markdown
feat Add border to import label
```

**Good**
```markdown
feat: Add border to import label
```

## 3. Limit the subject line to 50 characters

50 characters is not a hard limit, just a rule of thumb. Keeping subject lines at this length ensures that they are readable, and forces the author to think for a moment about the most concise way to explain what’s going on.

## 4. Capitalize the subject line

Begin all subject lines with a capital letter.

**Bad**
```markdown
feat: add border to import label

```

**Good**
```markdown
feat: Add border to import label
```

## 5. Do not end the subject line with a period

Trailing punctuation is unnecessary in subject lines. Besides, space is precious when you’re trying to keep them to 50 chars or less.

**Bad**
```markdown
feat: Add border to import label.

```

**Good**
```markdown
feat: Add border to import label
```

## 6. Use the imperative mood in the subject line

Imperative mood just means “spoken or written as if giving a command or instruction”. 

**Bad**
```markdown
Added style for hero, reviews, partners block, divided blocks on section names: -cover.html, -hero.html etc
```

**Good**
```markdown
Add style for hero, reviews, partners block, divided blocks on section names: -cover.html, -hero.html etc
```