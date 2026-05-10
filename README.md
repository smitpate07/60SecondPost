# 🚀 60SecPost — AI-Powered Instagram Publisher for Small Businesses

> **Turn a raw photo into a publish-ready Instagram post in under 60 seconds — no designer, no copywriter, no scheduling tool.**

> Built on self-hosted N8N · Google Gemini · Telegram · Meta Graph API

---

## 📌 Problem Statement

Posting consistently to Instagram is one of the most time-consuming parts of social media management. The bottleneck is rarely taking the photo — it is writing a caption that resonates, then researching and adding the right hashtags to maximize reach. For a solo creator, small business, or marketing team managing multiple accounts, this ritual repeats every single day.

**The typical manual process:**

1. Take or select a photo
2. Open Instagram (or a scheduling tool)
3. Write a caption from scratch — usually 5–10 minutes of staring at a blank box
4. Research relevant hashtags — another 3–5 minutes
5. Upload, preview, and publish

**The result:** A task that should feel quick takes 10–15 minutes of focused attention, multiple times per week.

---

 ## The Solution

The N8N workflow eliminates steps 2–5 entirely. You send a photo to a private Telegram bot, and within seconds:

- **Gemini 2.5 Flash** analyzes the image using computer vision and generates a compelling 2–3 sentence caption tailored to the photo's content, mood, and subject.
- Gemini also generates 10 targeted hashtags relevant to the image.
- The photo is published directly to your Instagram Business/Creator account via the official Facebook Graph API
- Your Telegram bot replies with a confirmation showing exactly what was posted

---

## 🗺️ High-Level N8N Workflow

![highlevel](highlevel.png)

---


## 💰 Business Impact

| Metric | Before PostPilot | After PostPilot |
|--------|-----------------|-----------------|
| Time per Instagram post | 45–90 mins | < 60 seconds |
| Cost per post (designer/copywriter) | $15–$50 | ~$0.05 (API cost) |
| Posts per week (realistic for 1 person) | 2–3 | 10–14 |
| Consistency of brand voice | Variable | AI-standardised |
| Technical skill to operate | Medium | None — just Telegram |
| Monthly content cost | $600–$2,000 | ~$2.00 |

---

## 🛠️ Tech Stack

| Tool | Role | Why it was chosen |
|------|------|------------------|
| **N8N (self-hosted)** | Workflow automation engine | Free, self-hosted, full data control, no vendor lock-in |
| **Telegram Bot API** | User interface | Universal, zero installation, instant notifications, inline keyboards |
| **Google Gemini 2.5 Flash** | Image editing + caption generation | Best multimodal model, single API key covers both image and text tasks |
| **Meta Graph API** | Instagram publishing | Only official method for automated posting, completely free |
| **imgbb API** | Temporary image hosting | Meta requires a public HTTPS URL — imgbb is free, images deleted immediately after posting |

### Why self-hosted N8N over cloud tools?

- **Data privacy** — images and captions never leave your server
- **No execution limits** — Zapier/Make charge per workflow run
- **Full customisation** — every node, every expression is configurable
- **Cost** — $5–$10/month VPS vs $50–$200/month for equivalent cloud automation

---

## ⚙️ How It Works

### Phase 1 — Photo Submission
User sends a photo to the Telegram bot with an edit prompt as the caption. The bot confirms receipt and begins processing.

### Phase 2 — AI Image Editing
The photo is downloaded from Telegram and sent to Gemini 2.5 Flash with the user's instruction. Gemini edits the image — background changes, lighting, colour grading — while preserving faces and people.

### Phase 3 — Caption Generation
The edited image is analysed by Gemini to generate an engaging Instagram caption (under 150 characters) and 10 relevant hashtags tailored to the image and user intent.

### Phase 4 — Preview & Approval
The edited image is sent back to the user in Telegram as a preview with two buttons: **✅ Approve & Post** and **✏️ Edit**.

### Phase 5a — Approve Path
Image is temporarily hosted on imgbb to get a public URL → Instagram media container created → 5 second processing wait → published → imgbb image deleted → Telegram confirmation sent.

### Phase 5b — Edit Path
Bot asks user to describe changes → re-runs full AI pipeline with new instructions → sends fresh preview with Approve/Edit buttons again.

---

## 💰 Cost Estimate (10 posts/week)

| Service | Cost |
|---------|------|
| Google Gemini 2.5 Flash | ~$0.00 (free tier) |
| Gemini Image Editing | ~$1.00 |
| imgbb, Meta API, Telegram | $0.00 (all free) |
| N8N self-hosted | $0.00 |
| **Total** | **~$6–$10/month** |

---

## ⚠️ Known Limitations

- Instagram token expires every 60 days — manual refresh required.
- Gemini image editing may alter faces slightly — works best with landscape/product shots

---

## 🎥 Demo Video

<div>
    <a href="https://www.loom.com/share/0f98a057cd2745a39effd6ab5504fa7a">
      <p></p>
    </a>
    <a href="https://www.loom.com/share/0f98a057cd2745a39effd6ab5504fa7a">
      <img style="max-width:300px;" src="https://cdn.loom.com/sessions/thumbnails/0f98a057cd2745a39effd6ab5504fa7a-7564f4ccd32a27bc.jpg#t=0.1">
    </a>
  </div>

> ▶️ Click the image above to watch the full demo — one photo, one prompt, live on Instagram in under 60 seconds. No agency. No designer. Just automation.
---
*Built to give every small business owner a social media team in their pocket — without the agency price tag.*