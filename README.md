# SJA Legal — Insights Content Repository

This repository stores all articles published in the **Insights / Knowledge Centre** section of the SJA Legal website.

---

## Repository Structure

```
articles/
  index.json          ← Master list of all articles (metadata only)
  article-id.md       ← One Markdown file per article (full content)
```

---

## How to Add a New Article

### Step 1 — Create the Markdown file

In the `articles/` folder, create a new file named with a short, URL-friendly ID:

**Naming rules:**
- Lowercase letters only
- Use hyphens instead of spaces
- No special characters
- Keep it short and descriptive

**Examples:**
- `gst-input-tax-credit-2025.md`
- `fema-overseas-investment-rules.md`
- `ibc-resolution-plan-approval.md`

**File contents** — write your article in Markdown:

```markdown
## Introduction

Your opening paragraph here...

---

## Section Heading

Content with **bold**, *italic*, and > blockquotes as needed.

### Sub-heading

- Bullet point one
- Bullet point two

| Column A | Column B |
|----------|----------|
| Row 1    | Data     |
```

---

### Step 2 — Add an entry to `index.json`

Open `articles/index.json` and add a new entry to the array. **Add new articles at the top** so they appear first on the website.

```json
{
  "id": "your-article-id",
  "title": "Full Title of the Article",
  "tag": "GST",
  "year": 2025,
  "date": "Apr 2025",
  "author": "SJA Legal",
  "excerpt": "A one or two sentence summary shown on the article card.",
  "published": true
}
```

**Field reference:**

| Field | Required | Description |
|-------|----------|-------------|
| `id` | ✅ | Must exactly match the `.md` filename (without `.md`) |
| `title` | ✅ | Full article title |
| `tag` | ✅ | Practice area — see list below |
| `year` | ✅ | Publication year as a number, e.g. `2025` |
| `date` | ✅ | Month and year, e.g. `"Apr 2025"` |
| `author` | ✅ | Author name, e.g. `"SJA Legal"` |
| `excerpt` | ✅ | 1–2 sentence summary shown on cards |
| `published` | ✅ | `true` to show publicly, `false` to hide |

**Available practice area tags:**
- `Direct Tax`
- `GST`
- `Customs`
- `FEMA & Regulatory`
- `IBC & Insolvency`
- `PMLA & Benami`
- `International Tax`
- `Transfer Pricing`
- `General`

---

### Step 3 — Commit your changes

Commit both the new `.md` file and the updated `index.json`. The website fetches directly from this repository and will show the new article within seconds of the commit going live.

---

## How to Edit an Existing Article

1. Open the relevant `.md` file in `articles/`
2. Make your changes
3. To update metadata (title, excerpt, date, tag), also edit the corresponding entry in `index.json`
4. Commit

---

## How to Unpublish an Article

In `index.json`, find the article's entry and set `"published": false`. The article will no longer appear on the website. The file remains in the repository and can be re-published at any time by setting it back to `true`.

---

## Markdown Reference

| Syntax | Output |
|--------|--------|
| `## Heading` | Section heading |
| `### Sub-heading` | Sub-section heading |
| `**bold**` | **bold** |
| `*italic*` | *italic* |
| `> quoted text` | Blockquote (styled in rust/orange) |
| `---` | Horizontal divider |
| `- item` | Bullet list |
| `1. item` | Numbered list |
| `\| Col \| Col \|` | Table |

---

## Website Configuration

The website HTML file contains the following configuration block near the top of the script:

```js
const GITHUB = {
  owner: 'YOUR_GITHUB_USERNAME',
  repo:  'YOUR_REPO_NAME',
  branch: 'main',
  path: 'articles'
};
```

Update `owner` and `repo` to match this repository. This only needs to be done once.
