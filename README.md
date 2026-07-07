# 🤖 AI Newsletter Automation

An end-to-end, prompt-driven workflow that researches, assembles, and formats a weekly AI newsletter — from raw source gathering all the way to a production-ready HTML email.

Three chained AI agent prompts turn a folder of historical performance data and content ideas into a fully designed, send-ready newsletter (HTML + plain-text), pulling live material from the web, arXiv, GitHub, Product Hunt, and X/Twitter along the way.

---

## ✨ What this does

Instead of a human manually digging through news sites, arXiv, GitHub trending, Product Hunt, and Twitter every week, this workflow automates the full newsletter production pipeline in three stages:

1. **Research** — gather and summarize the week's most relevant AI news, papers, repos, products, and tweets, guided by what has historically performed well.
2. **Assembly** — turn that raw research into a polished, edited newsletter draft with a consistent voice and structure.
3. **Design** — convert the finalized draft into a responsive, email-client-safe HTML file (plus a plain-text fallback), ready to drop into an ESP (email service provider).

Each stage is driven by a standalone prompt (see [`prompts/`](./prompts)), so the whole pipeline can be run by any capable AI agent with access to the right tools (web search, Google Drive, Gmail, arXiv, GitHub, Product Hunt).

---

## 🗂️ Repository structure

```
ai-newsletter-automation/
├── prompts/                          # The 3 prompts that drive the pipeline
│   ├── AI_Newsletter_Research_Prompt.pdf
│   ├── Design_Phase_Prompt.pdf
│   └── Final_Draft_Prompt.pdf
│
├── gDriveFiles/                      # Historical inputs (read from Google Drive)
│   ├── AI_Newsletter_Performance.pdf     # Past issue performance (opens, clicks, subs)
│   └── AI_Newsletter_Content_Ideas.pdf   # Bank of high-potential content themes
│
├── research/                         # Stage 1 output — raw research results
│   ├── newsletter_web_research_results.md   # Big story + quick updates
│   ├── newsletter_research_papers.md        # Featured arXiv papers
│   ├── newsletter_github_repos.md           # Trending GitHub repos
│   ├── newsletter_ai_products.md            # Trending Product Hunt launches
│   └── newsletter_twitter_highlights.md     # Top tweets from AI leaders & community
│
├── final_draft/                      # Stage 2 output — assembled newsletter
│   └── AI_Newsletter_This_Week.md        # Full markdown draft (final content + links)
│
├── output/                           # Stage 3 output — production-ready email
│   ├── AI_Newsletter_<YYYY-MM-DD>.html   # Responsive, inlined-CSS HTML email
│   └── AI_Newsletter_<YYYY-MM-DD>.txt    # Plain-text fallback
│
├── LICENSE
└── README.md
```

---

## 🔄 The pipeline

### Stage 1 — Research (`AI_Newsletter_Research_Prompt.pdf`)

Reads historical performance data and content ideas from Google Drive, checks recent inbox feedback for recurring reader requests, and uses that to pick a focus area for the week. Then researches:

| Source | Output |
|---|---|
| Web search | 1 Big Story + 3–5 Quick Updates, each with a source link |
| arXiv | 1–3 featured research papers with impact analysis |
| GitHub | 3–5 trending repos matching the focus area |
| Product Hunt | 3–5 trending AI product launches |
| X / Twitter | 3–5 notable tweets from AI leaders & the community |

Each result set is saved as its own markdown file in [`research/`](./research).

### Stage 2 — Assembly (`Final_Draft_Prompt.pdf`)

Reads all five research files plus a preferred newsletter template/structure, then writes a single cohesive issue — intro, section headers, editorial transitions, and every source link preserved — saved to [`final_draft/AI_Newsletter_This_Week.md`](./final_draft).

### Stage 3 — Design (`Design_Phase_Prompt.pdf`)

Converts the finalized markdown into a send-ready email:

- **HTML** — 600px table-based layout, inlined CSS, mobile media queries, bulletproof VML button for Outlook, UTM-tagged links, `{{web_version_url}}` / `{{unsubscribe_url}}` / `{{sender_address}}` placeholders.
- **Plain-text** — wrapped fallback version with links on their own line, for clients that block HTML.

Both are saved to [`output/`](./output), named `AI_Newsletter_<YYYY-MM-DD>.html` / `.txt`.

---

## 🧰 Tools & data sources used

- **Google Drive** — historical performance data & content idea bank
- **Gmail** — scanning for reader feedback signals
- **Web search** — breaking AI news
- **arXiv** — recent research papers
- **GitHub** — trending repositories
- **Product Hunt** — trending AI product launches
- **X / Twitter** — community and industry commentary
- **Model Context Protocol (MCP)** — the connector layer used to reach the above tools from the agent

## 🚀 How to use

1. Drop your own historical performance + content-idea files into a Drive folder.
2. Run the **Research** prompt against your AI agent of choice (with web/Drive/Gmail/arXiv/GitHub/Product Hunt/Twitter access) → produces the five files in `research/`.
3. Run the **Final Draft** prompt, pointing it at the research files (and optionally a sample newsletter template) → produces `final_draft/AI_Newsletter_This_Week.md`.
4. Run the **Design** prompt against the final draft → produces the HTML + plain-text email in `output/`.
5. Fill in the `{{web_version_url}}`, `{{unsubscribe_url}}`, and `{{sender_address}}` placeholders and load the HTML into your ESP of choice.

## 📄 License

Released under the [MIT License](./LICENSE).
