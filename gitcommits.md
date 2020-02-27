# Git commit message writing convention

These guideline are based on [How to Write a Git Commit Message](https://github.com/cbeams/chris.beams.io/blob/master/_posts/2014-08-31-git-commit.md) article.

## Commit message structure

Commit message should have following structure:

```markdown
JIRA-ID:Commit message subject line

Commit message body.
```

## Commit message rules

1. [Start Commit message subject line from Jira issue key (GitHub issue ID)](#1-commit-message-subject-line-should-start-from-jira-issue-key)
2. [Separate Jira issue key and Commit message subject line by a colon and blank](#2-separate-jira-issue-key-and-commit-message-subject-line-by-a-colon-and-blank)
3. [Write Jira issue key in uppercase](#3-write-jira-issue-key-in-uppercase)
4. [Separate subject from body with a blank line](#4-separate-subject-from-body-with-a-blank-line)
5. [Limit the subject line to 50 characters](#5-limit-the-subject-line-to-50-characters)
6. [Capitalize the subject line](#6-capitalize-the-subject-line)
7. [Do not end the subject line with a period](#7-do-not-end-the-subject-line-with-a-period)
8. [Use the imperative mood in the subject line](#8-use-the-imperative-mood-in-the-subject-line)
9. [Wrap the body at 72 characters](#9-wrap-the-body-at-72-characters)
10. [Use the body to explain what and why vs. how](#10-use-the-body-to-explain-what-and-why-vs-how)

### 1. Commit message subject line should start from Jira issue key

If your commit is related to a Jira task or GitHub issue, put the Jira key or GitHub issue ID at the beginning of the Commit message subject line. This will help link your commit and task.

**Bad**

```markdown
Add phones support to order list (VP-1510)
```

**Good**

```markdown
VP-1510: Add phones support to order list
```

### 2. Separate Jira issue key and Commit message subject line by a colon and blank

If Jira issue key (GitHub issue ID) used separate it from Commit message subject line by a colon and blank.

**Bad**

```markdown
VP-1510 Add phones support to order list
```

**Good**

```markdown
VP-1510: Add phones support to order list
```

### 3. Write Jira issue key in uppercase

To link automatically you commit to Jira task you should write Jira issue key in uppercase.

**Bad**

```markdown
vp-1380: Add customer to order email notification
```

**Good**

```markdown
VP-1380: Add customer to order email notification
```

### 4. Separate subject from body with a blank line

Not every commit requires both a subject and a body. Sometimes a single line is fine, especially when the change is so simple that no further context is necessary.

```markdown
VP-1254: Change address format to US standard one
```

When a commit merits a bit of explanation and context, you need to write a body.

```markdown
Filter prices by applicable pricelists to optimize evaluation

EvaluateProductPrices() now fetches prices from applicable pricelists only (instead of fetching all product prices for applicable products). This might reduce the evaluation time when there are lots of pricelists.
```

### 5. Limit the subject line to 50 characters

50 characters is not a hard limit, just a rule of thumb. Keeping subject lines at this length ensures that they are readable, and forces the author to think for a moment about the most concise way to explain what’s going on.

### 6. Capitalize the subject line

Begin all subject lines with a capital letter.

**Bad**

```markdown
VP-1502: make layout page for login,reset password page

```

**Good**

```markdown
VP-1502: Make layout page for login,reset password page
```

### 7. Do not end the subject line with a period

Trailing punctuation is unnecessary in subject lines. Besides, space is precious when you’re trying to keep them to 50 chars or less.

**Bad**

```markdown
Change BASE_URL in theme layout.

```

**Good**

```markdown
Change BASE_URL in theme layout
```

### 8. Use the imperative mood in the subject line

Imperative mood just means “spoken or written as if giving a command or instruction”. A few examples:

```markdown
Clean your room
Close the door
Take out the trash
```

The imperative can sound a little rude; that’s why we don’t often use it. But it’s perfect for Git commit subject lines. One reason for this is that Git itself uses the imperative whenever it creates a commit on your behalf.

To remove any confusion, here's a simple rule to get it right every time.

A properly formed Git commit subject line should always be able to complete the following sentence:

```markdown
If applied, this commit will *your subject line here*
```

**Bad**

```markdown
Added style for hero, reviews, partners block, divided blocks on section names: -cover.html, -hero.html etc

```

**Good**

```markdown
Add style for hero, reviews, partners block, divided blocks on section names: -cover.html, -hero.html etc
```

*Remember: Use of the imperative is important only in the subject line. You can relax this restriction when you’re writing the body.*

### 9. Wrap the body at 72 characters

Git never wraps text automatically. When you write the body of a commit message, you must mind its right margin, and wrap text manually.

The recommendation is to do this at 72 characters, so that Git has plenty of room to indent text while still keeping everything under 80 characters overall.

### 10. Use the body to explain what and why vs. how

In most cases, you can leave out details about how a change has been made. Code is generally self-explanatory in this regard. Just focus on making clear the reasons why you made the change in the first place—the way things worked before the change (and what was wrong with that), the way they work now, and why you decided to solve it the way you did.

```markdown
Filter prices by applicable pricelists to optimize evaluation

EvaluateProductPrices() now fetches prices from applicable pricelists only (instead of fetching all product prices for applicable products). This might reduce the evaluation time when there are lots of pricelists.
```
