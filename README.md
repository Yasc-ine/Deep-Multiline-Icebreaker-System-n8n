# Deep Multiline Icebreaker System (n8n Workflow)


An **advanced, AI-powered cold outreach personalization workflow** built in **n8n** that scrapes a company's website, summarizes key pages, and generates **deeply personalized, multi-line email icebreakers** using GPT-4.1 — all automated from LinkedIn-style lead data.

---

## 🎯 Purpose

Generate **highly personalized cold email openers** that prove you've *actually* researched the prospect by referencing **non-obvious details** from their website. Avoid generic fluff like “Love your site!” — instead, reference specific services, values, tech stacks, or white-label offerings.

> Example output:
> ```
> Hey Aina,
>
> Love what you're doing at Maki. Also doing some outsourcing right now, wanted to run something by you.
>
> So I hope you'll forgive me, but I creeped you/Maki quite a bit. I know that discretion is important to you guys (or at least I'm assuming this given the part on your website about white-labelling your services) and I put something together a few months ago that I think could help...
> ```

---

## 🚀 How It Works

```mermaid
graph TD
    A[Start: Get Search URL] --> B[Apify LinkedIn Scraper]
    B --> C[Filter: Has Website + Email]
    C --> D[Scrape Homepage]
    D --> E[Extract All <a> Links]
    E --> F[Split & Filter Relative Links]
    F --> G[Normalize URLs]
    G --> H[Remove Duplicates]
    H --> I[Limit to 3 Pages]
    I --> J[HTTP Request Each Page]
    J --> K[Convert to Markdown]
    K --> L[GPT-4.1: Summarize Page]
    L --> M[Aggregate Summaries]
    M --> N[GPT-4.1: Generate Icebreaker]
    N --> O[Append to Google Sheets]
    O --> P[Loop Next Lead]
