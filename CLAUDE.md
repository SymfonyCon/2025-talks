# Task: Create SymfonyCon 2026 Talks Repository

## Inputs:
- Previous year repo: https://github.com/symfonycon/2025-talks
- Schedule: https://live.symfony.com/2026-[city]-con/schedule
- Check main branch first for any existing content

## Requirements:

### 1. Format Verification (DO THIS FIRST!)
```bash
# Check 2025 format with visible characters to see trailing spaces
curl -s "https://raw.githubusercontent.com/symfonycon/2025-talks/main/README.md" | head -100 | cat -A
```

### 2. Check Main Branch
- Fetch main branch first: `git fetch origin main`
- See what talks/content already exist
- Note any real slides/blog post links to preserve

### 3. Header Section
- Update year, city, dates in title and social search links
- Keep IMPORTANT and NOTE blocks with correct dates

### 4. Fetch Schedule
- Get all talks from live.symfony.com schedule
- Extract: title, speaker(s), description, time/track

### 5. Speaker Details (in order of efficiency)
a) **Check 2025 repo first** - extract all speaker sections from previous year
b) **For returning speakers** - reuse their complete contact info
c) **For new speakers** - use web search or agent to find:
   - GitHub username (check for sponsors badge)
   - Personal website/blog (check for RSS feed)
   - Social media: Bluesky, Twitter/X, Mastodon, LinkedIn

### 6. Formatting Rules (CRITICAL!)
**Lines that need 2 trailing spaces (  ):**
- `By [Name](url)  `
- `💻 on ...  `
- `✍ on ...  ` or `_✍ blog not found_  `

**Lines with NO trailing spaces:**
- `💬 on ...` (first social line)
- `· ...` (all subsequent social lines with middle dot)

**Special formats:**
- GitHub sponsors: `<sup>[💚](https://github.com/sponsors/username)</sup>`
- RSS feeds: `<sup>[![rss](icon/rss.svg)](feed-url)</sup>`
- Blog not found: `_✍ blog not found_  ` (italics + 2 spaces)

### 7. Content Status
- Use `~~Slides~~` for unavailable content
- Use `[Slides](url)` when actual link exists
- Check main branch for any real content that was added

### 8. Verification
```bash
# Verify trailing spaces are correct
sed -n '/^By \[/,/^---/p' README.md | head -20 | cat -A
```

### 9. Git Workflow
- Work on branch: `claude/add-2026-talks-[session-id]`
- Commit in batches (header, talks, speaker details batch 1, 2, 3)
- Merge main branch content before pushing
- Push to designated branch

## Output Format Example:
```markdown
## Talk Title

<dl>
  <dt>Description</dt>
  <dd>Talk description here...</dd>
</dl>

~~Slides~~
~~Video~~
~~Blog post~~

By [Speaker Name](https://connect.symfony.com/profile/username)
💻 on [![github](icon/github.svg) @username](https://github.com/username)  <sup>[💚](https://github.com/sponsors/username)</sup>
✍ on [🌐 website.com](https://website.com)  <sup>[![rss](icon/rss.svg)](https://website.com/feed)</sup>
💬 on [![bluesky](icon/bluesky.svg) @user.bsky.social](https://bsky.app/profile/user.bsky.social)
· [![twitter](icon/twitter.svg) @user](https://twitter.com/user)
· [![mastodon](icon/mastodon.svg) @user@server](https://server/@user)
· [![linkedin](icon/linkedin.svg) @user](https://linkedin.com/in/user)
```

## Quality Checks:
- [ ] All talks from schedule included
- [ ] Trailing spaces correct (`cat -A` to verify)
- [ ] All returning speakers have full details
- [ ] Main branch content merged
- [ ] Commits pushed to correct branch
