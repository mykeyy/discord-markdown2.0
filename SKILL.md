---
name: discord-markdown2.0
description: Master Discord's Markdown formatting system including text styling, headers, lists, code blocks, block quotes, spoiler tags, and syntax highlighting. Use when writing formatted Discord messages, server announcements, bot responses, embed descriptions, or any content intended for Discord chat.
---

# discord-markdown

Complete reference for Discord's Markdown formatting — covering text styling, organizational elements, code blocks, spoilers, and syntax highlighting for writing polished, readable Discord messages.

## When to Use This Skill

- Writing formatted server announcements or rules channels
- Crafting bot message templates or embed descriptions
- Creating readable changelogs or patch notes in Discord
- Formatting code snippets shared in dev/tech channels
- Writing staff documentation or onboarding messages
- Building structured community posts (events, tournaments, etc.)
- Generating Discord message content programmatically

---

## Text Formatting

The building blocks of Discord Markdown. These work inline anywhere in a message.

| Style | Syntax | Output |
|---|---|---|
| Italic | `*text*` or `_text_` | *text* |
| Bold | `**text**` | **text** |
| Bold Italic | `***text***` | ***text*** |
| Underline | `__text__` | <u>text</u> |
| Underline Italic | `__*text*__` | <u>*text*</u> |
| Underline Bold | `__**text**__` | <u>**text**</u> |
| Underline Bold Italic | `__***text***__` | <u>***text***</u> |
| Strikethrough | `~~text~~` | ~~text~~ |
| Spoiler | `\|\|text\|\|` | *(hidden until clicked)* |

### Escaping Markdown

Prefix any character with `\` to render it literally:

```
\*this won't be italic\*
```

Or wrap the whole thing in a code block to suppress all formatting.

---

## Headers

Headers only work at the **start of a new line**. They do not render mid-sentence.

```
# Big Header
## Medium Header
### Small Header
```

**Rules:**
- `#` = largest heading
- `##` = medium heading
- `###` = smallest heading
- Must be the very first character on the line (no leading spaces)

---

## Subtext

Renders smaller, muted text below regular content. Good for footnotes or context.

```
-# This is subtext
```

**Rules:**
- Must start with `-# ` (dash, hash, space)
- The space after `#` is required
- Only works at the beginning of a line

---

## Masked Links (Hyperlinks)

Make text clickable with a custom label.

```
[Visit Google](https://google.com)
[Join our server](https://discord.gg/example)
```

To post a raw URL **without** an embed preview, wrap it in angle brackets:

```
<https://google.com>
```

---

## Lists

### Unordered Lists

Use `-` or `*` at the start of each line. Indent with **two spaces** for nested items.

```
- Item one
- Item two
  - Nested item
  - Another nested
- Item three
```

### Ordered Lists

Use `number.` format. Numbers don't need to be sequential — Discord auto-increments from the first number.

```
1. First item
2. Second item
3. Third item
```

You can also repeat `1.` and Discord will still number them correctly:

```
1. First
1. Second
1. Third
```

Mixed ordered/unordered is also supported — start with numbers then switch to dashes:

```
1. Step one
2. Step two
- Sub-note A
- Sub-note B
```

---

## Code Blocks

### Inline Code

Wrap with single backticks for inline code snippets:

```
Use `npm install` to install dependencies.
```

### Multiline Code Blocks

Wrap with triple backticks for multi-line blocks:

````
```
function hello() {
  console.log("Hello, Discord!")
}
```
````

---

## Syntax Highlighting

Add a language name right after the opening triple backticks:

````
```js
const greet = (name) => `Hello, ${name}!`
```
````

````
```py
def greet(name):
    return f"Hello, {name}!"
```
````

### Supported Languages

Common ones you'll use most:

| Language | Tag |
|---|---|
| JavaScript | `js` or `javascript` |
| TypeScript | `ts` or `typescript` |
| Python | `py` or `python` |
| Bash / Shell | `bash` or `sh` |
| JSON | `json` |
| CSS | `css` |
| HTML / XML | `html` / `xml` |
| C++ | `cpp` |
| C# | `cs` |
| YAML | `yaml` |
| Markdown | `md` |
| Diff | `diff` |
| INI / Config | `ini` |
| SQL | `sql` |
| Rust | `rust` |
| Go | `go` |

> ⚠️ Syntax highlighting is **not visible on mobile** Discord clients.

For a full list of supported languages: https://github.com/cherryblossom000/discord-syntax-highlighting

---

## Block Quotes

### Single-line Block Quote

```
> This is a single-line quote.
```

### Multi-line Block Quote

```
>>> Everything from here
will be quoted
until the end of the message.
```

**Use cases:**
- Quoting someone's message for context
- Highlighting important callouts
- Adding visual separation to sections

---

## Spoiler Tags

Hide text behind a click-to-reveal blur. Useful for game spoilers, surprise announcements, etc.

```
||This is a spoiler!||
```

Can also combine with other formatting:

```
||**Bold spoiler!**||
```

> Spoiler tags are **negated inside code blocks** — the text will show as-is.

---

## Timestamps

Render dynamic, localized timestamps that adjust to each user's timezone.

```
<t:UNIX_TIMESTAMP:FORMAT>
```

| Format Flag | Display Style | Example |
|---|---|---|
| `t` | Short time | 9:41 AM |
| `T` | Long time | 9:41:00 AM |
| `d` | Short date | 05/01/2026 |
| `D` | Long date | May 1, 2026 |
| `f` | Short date/time | May 1, 2026 9:41 AM |
| `F` | Full date/time | Friday, May 1, 2026 9:41 AM |
| `R` | Relative | 3 hours ago / in 2 days |

**Example:**

```
Event starts: <t:1746076800:F>
Starts <t:1746076800:R>
```

Get a Unix timestamp from https://www.unixtimestamp.com or `Date.now() / 1000` in JS (rounded to integer).

---

## Mentions

| Type | Syntax |
|---|---|
| User | `<@USER_ID>` |
| Role | `<@&ROLE_ID>` |
| Channel | `<#CHANNEL_ID>` |
| Server Guide | `<id:guide>` |
| Browse Channels | `<id:browse>` |
| Customize | `<id:customize>` |
| Linked Roles | `<id:linked-roles>` |

---

## Practical Examples

### Server Announcement

```
# 🎉 Tournament Registration Open

**Valorant Community Cup Season 3** is now accepting sign-ups!

- 📅 Date: <t:1746076800:F>
- 🗓️ Registration closes: <t:1745990400:R>
- 💰 Prize pool: **₱5,000**

> ⚠️ Teams must register before the deadline — no exceptions.

[Register here](https://forms.gle/example)

-# Organized by the Alley SMP Staff Team
```

### Patch Notes / Changelog

```
# v2.1.0 — Patch Notes

### ✅ Added
- New `/roster` command for team management
- Auto-DM confirmation on registration

### 🔧 Fixed
- Duplicate entry bug on re-registration
- Timezone offset in timestamp display

### ❌ Removed
- Legacy `!register` prefix command

-# Full changelog: <https://github.com/example/repo>
```

### Code Snippet Share

````
Found the bug — it was a missing `await`:

```js
// ❌ Before
const data = fetchRoster(teamId)

// ✅ After
const data = await fetchRoster(teamId)
```

cc <@USER_ID>
````

---

## Common Pitfalls

1. **Headers not rendering** — Must be at the very start of the line, no leading spaces or characters
2. **Subtext not working** — Space after `-#` is required: `-# text` not `-#text`
3. **Underline looks like a link** — `__text__` underlines in Discord, not `<u>` tags
4. **Syntax highlighting on mobile** — It won't show; plain code block still renders fine
5. **List indentation** — Requires **two spaces** as of late 2025 (one space no longer works)
6. **Spoilers in code blocks** — `||spoiler||` inside backticks will render as literal text
7. **Masked links in embeds** — Masked links only work in message content, not all embed fields

---

## Webhook / API Payloads

When sending messages via Discord webhooks or the bot API, messages are structured as JSON. Below are common payload patterns.

### Simple Message (No Embed)

Plain text message with no embed attached.

```json
{
  "content": "Hello, this is a plain message!",
  "embeds": [],
  "attachments": []
}
```

### Message with Basic Embed

An embed with a description and a custom color.

```json
{
  "content": "Check out this update!",
  "embeds": [
    {
      "title": "System Update",
      "description": "A new version has been deployed successfully.",
      "color": 5814783
    }
  ],
  "attachments": []
}
```

### Message with Rich Embed

Full embed with fields, footer, timestamp, and author info.

```json
{
  "content": "Server status report",
  "embeds": [
    {
      "title": "Server Status",
      "description": "All systems are operational.",
      "color": 3066993,
      "author": {
        "name": "Status Bot",
        "icon_url": "https://example.com/bot-icon.png"
      },
      "fields": [
        {
          "name": "Uptime",
          "value": "99.98%",
          "inline": true
        },
        {
          "name": "Latency",
          "value": "42ms",
          "inline": true
        },
        {
          "name": "Players Online",
          "value": "1,247",
          "inline": true
        }
      ],
      "footer": {
        "text": "Last checked",
        "icon_url": "https://example.com/footer-icon.png"
      },
      "timestamp": "2026-05-01T12:00:00.000Z"
    }
  ],
  "attachments": []
}
```

### Embed Color Codes

Common colors used for embeds:

| Purpose | Decimal | Hex | Preview |
|---|---|---|---|
| Green (Success) | `3066993` | `#2ECC71` | 🟢 |
| Red (Error) | `15158332` | `#E74C3C` | 🔴 |
| Blue (Info) | `3447003` | `#3498DB` | 🔵 |
| Orange (Warning) | `15105570` | `#E67E22` | 🟠 |
| Purple (Custom) | `10181046` | `#9B59B6` | 🟣 |
| Yellow (Highlight) | `15844367` | `#F1C40F` | 🟡 |
| Default (Dark) | `5793266` | `#5865F2` | ⚫ |

### Payload Rules

- `content` max length: **2000 characters**
- Embed max `description` length: **4096 characters**
- Max **10 embeds** per message
- Max **25 fields** per embed
- Field `name` max: **256 characters**
- Field `value` max: **1024 characters**
- `color` must be a base-10 integer (not hex string)
- `timestamp` must be ISO 8601 format

---

## Quick Reference Card

```
**bold**          __underline__        *italic*
***bold italic*** ~~strikethrough~~    ||spoiler||

# H1   ## H2   ### H3
-# subtext

> quote          >>> multiline quote

- unordered      1. ordered
  - nested         2. list

`inline code`
```multiline code```
```lang (syntax highlight)```

[label](url)     <url> (no embed)
<t:timestamp:F>  (dynamic time)
```
