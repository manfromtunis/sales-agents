# sales-agents

AI-powered sales skills that turn meeting notes into actionable pipeline intelligence. Built for Claude Code.

Parse your Gemini Meet notes, Claap transcripts, or any markdown meeting notes to generate deal reviews, sales decks, battle cards, and documentation gap analyses — all from one command.

## Skills

| Skill | Command | What it does |
|-------|---------|-------------|
| **Weekly Deal Review** | `/weekly-deal-review` | Parse notes → pipeline summary table + deal cards |
| **Sales Deck** | `/sales-deck <prospect>` | Generate prospect-specific 8-slide deck from real verbatims |
| **Battle Cards** | `/battle-cards` | Competitive intelligence cards with objection scripts |
| **Help Center Gaps** | `/help-center-gaps` | Find doc gaps from prospect questions, generate article briefs |
| **Sales Pipeline** | `/sales-pipeline` | Run all skills → unified weekly report |

## Install

**All skills:**
```bash
npx skills add manfromtunis/sales-agents
```

**Individual skill:**
```bash
npx skills add manfromtunis/sales-agents@weekly-deal-review
npx skills add manfromtunis/sales-agents@sales-deck
npx skills add manfromtunis/sales-agents@battle-cards
npx skills add manfromtunis/sales-agents@help-center-gaps
npx skills add manfromtunis/sales-agents@sales-pipeline
```

## Configuration

All configuration is optional. Skills work out of the box with sensible defaults.

| Env Variable | Default | Description |
|-------------|---------|-------------|
| `MEETING_NOTES_PATH` | `./meeting-notes/` | Directory containing .md meeting notes |
| `DOCS_PATH` | *(none)* | Path to existing docs/help center for gap cross-reference |
| `OUTPUT_FORMAT` | `markdown` | Default output: `markdown` or `notion` |
| `BRAND_SKILL` | *(none)* | Brand guidelines skill name (e.g., `clip2earn-brand`) |

## Quick Start

```bash
# 1. Point to your meeting notes
export MEETING_NOTES_PATH="./meeting-notes/"

# 2. Run the full pipeline
/sales-pipeline

# Or run individual skills
/weekly-deal-review
/sales-deck "Acme Corp"
/battle-cards --competitor "Competitor X"
/help-center-gaps --docs ./docs/ --issues
```

## Supported Note Formats

- **Gemini Meet notes** — French or English, with timestamps, attendee lists, structured sections
- **Claap transcripts** — Speaker labels with timestamps
- **Raw markdown** — Any .md file with meeting content

The parsing engine detects the format automatically and applies appropriate extraction patterns. See `references/meeting-parsing-guide.md` for the full pattern reference.

## Optional Integrations

These tools enhance the skills but are **not required** — everything falls back to markdown:

| Tool | Used by | What it adds |
|------|---------|-------------|
| **Notion MCP** | All skills | Output directly to Notion pages/databases |
| **WebSearch** | battle-cards | Enrich competitor cards with web research |
| **GitHub CLI (`gh`)** | help-center-gaps | Create GitHub issues for documentation gaps |
| **Brand skill** | sales-deck | Apply brand voice and visual guidelines to decks |

## Data Privacy

All processing happens locally. Meeting notes are read by Claude Code on your machine — nothing is sent to external services unless you explicitly use Notion or GitHub integrations. No data is stored between runs.

## Inspired By

Skills inspired by [Jeremy Goillot](https://www.linkedin.com/in/jeremygoillot/) (Allo) & [Pierre Touzeau](https://www.linkedin.com/in/pierretouzeau/) (Claap) — "6 agents IA qu'on utilise pour closer plus de deals".
