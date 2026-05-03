# 🚀 60SecPost — AI-Powered Instagram Publisher for Small Businesses

> **Turn a raw photo into a publish-ready Instagram post in under 60 seconds — no designer, no copywriter, no scheduling tool.**
> Built on self-hosted N8N · Google Gemini · Telegram · Meta Graph API

---

## 📌 The Problem

Small business owners waste **45–90 minutes per Instagram post** — editing photos, writing captions, researching hashtags, and manually uploading. Most give up and post inconsistently, killing their reach.

---

## 🎥 Demo Video

<div>
    <a href="https://www.loom.com/share/796f743b826a425bbccdd0b89f05bb07">
      <p></p>
    </a>
    <a href="https://www.loom.com/share/796f743b826a425bbccdd0b89f05bb07">
      <img style="max-width:300px;" src="https://cdn.loom.com/sessions/thumbnails/796f743b826a425bbccdd0b89f05bb07-b96e6b9358d0f4d5.jpg#t=0.1">
    </a>
  </div>

---


## 🗺️ High-Level N8N Workflow


---

## 💼 Use Case

A small business owner — restaurant, boutique, freelancer, creator — takes a photo on their phone. Instead of spending an hour editing it, writing a caption, and manually uploading, they:

1. Send the photo to a Telegram bot with a short prompt (e.g. *"Cozy café vibes, warm lighting"*)
2. The bot edits the image, writes a caption and 10 hashtags using AI
3. They review the preview and tap **✅ Approve & Post**
4. The post goes live on Instagram automatically

**Real-world example:** A restaurant posting daily specials used to spend 1 hour per post on photography editing and caption writing. With Telegram bot, the chef sends a photo from the kitchen — the post is live before the lunch rush.

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
- `/tmp` session storage clears on server restart — in-progress sessions will fail
- One image per post — carousel not yet supported
- Gemini image editing may alter faces slightly — works best with landscape/product shots

---

*Built to give every small business owner a social media team in their pocket — without the agency price tag.*