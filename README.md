<p align="center">
  <img src="cover.jpg" alt="fal.ai Video Generation" width="100%">
</p>

<h1 align="center">Day 4 — AI Video Generation</h1>
<p align="center">
  <strong>10 Days 10 Skills</strong> · Claude Code Course by <a href="https://bestguy.ai">Guy Aga</a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Service-fal.ai%20MCP-E63B2E?style=flat-square" alt="fal.ai">
  <img src="https://img.shields.io/badge/Skill-fal--ai--video--generation-111111?style=flat-square" alt="Skill">
  <img src="https://img.shields.io/badge/Level-Beginner-E8E4DD?style=flat-square&labelColor=111111" alt="Beginner">
</p>

---

## What is This?

This skill connects Claude Code to **fal.ai** — a platform with the world's best AI video models. Generate videos from text descriptions or images, using models like **Veo 3.1**, **Kling 3**, **Seedance**, and more.

This lesson also introduces **MCPs** — plugins that give Claude Code superpowers by connecting it to external services.

### What Can You Do With It?

| You Say | What Happens |
|---------|-------------|
| "Generate a 5-second video of a sunset" | Text → AI video via Veo 3.1 |
| "Animate this product image" | Your image → smooth video via Kling 3 |
| "Create first frame, then animate it" | Day 1 image gen → Day 4 video gen |
| "Make a cinematic intro for my brand" | Full production with all skills |

### What is an MCP?

Think of MCPs as **plugins for Claude Code**. Just like browser extensions add features to Chrome, MCPs add capabilities to Claude. In this case, the fal.ai MCP gives Claude access to 1000+ AI models — including the best video generators.

One command to install. Then Claude can use it.

---

## Prerequisites

- [ ] **Claude Code** (Pro or Max subscription)
- [ ] **fal.ai account** (requires credits — start with $5-10)
- [ ] **fal.ai API Key**

> **This skill costs money per video.** Video generation is more expensive than images. A 5-second video can cost $0.35 - $2.00 depending on the model. See pricing table below.

---

## Before You Start — Get Your fal.ai API Key

Do this first, before running any commands.

1. **Sign up** at [fal.ai](https://fal.ai)
2. **Add credits** at https://fal.ai/dashboard/usage-billing/credits ($5-10 to start — enough for 20-50 short test videos)
3. **Create an API key** at https://fal.ai/dashboard/keys → click **Create Key**
4. **Copy the key** (looks like `xxxx-xxxx:xxxxxxxxxxxx`) and save it somewhere safe — you will paste it into Phase 1 below

---

## Phase 1: Add the fal MCP Server

Run this command in **EITHER**:

- **(a)** A regular terminal (PowerShell, Terminal, Command Prompt), **OR**
- **(b)** A **fresh new conversation in Antigravity** — paste it as your first message and Claude will run it for you (approve if prompted)

```bash
claude mcp add --transport http fal-ai https://mcp.fal.ai/mcp --header "Authorization: Bearer YOUR_FAL_KEY"
```

Replace `YOUR_FAL_KEY` with the key you saved in the prerequisite step.

You should see a success message like `Added MCP server fal-ai`.

---

## Phase 2: Verify the MCP Is Connected

Open a **NEW conversation** in Claude Code or Antigravity.

> ⚠️ Even if you used Antigravity for Phase 1, you must open **another** new conversation now — Claude only loads MCP servers when a conversation starts, so the conversation that ran the install command won't see the new MCP yet.

In the new conversation, type:

```
/mcp
```

You should see **`fal-ai`** in the list of connected MCP servers.

**If it does NOT appear:**
- From a terminal, run `claude mcp list` — `fal-ai` should be in the output
- Check the config file at `~/.claude.json` (Mac/Linux) or `%USERPROFILE%\.claude.json` (Windows)
- Most common cause: typo in API key — re-run Phase 1

---

## Phase 3: Install the Skill

In the same conversation where `/mcp` showed `fal-ai`, paste this prompt:

```
Install the fal-ai-video-generation skill from https://github.com/guyaga/10d10s-day04-video-generation and verify the fal MCP is connected by searching for available video models.
```

Claude will clone the skill into `~/.claude/skills/` and run a model search through the fal MCP. You should see Veo 3.1, Kling 3, Seedance, LTX, and others.

---

## Phase 4: Generate Your First Video

Start with a **cheap model** (LTX or Kling 2.5) to dial in your prompt, then upgrade to premium models (Veo 3.1, Kling 3 Pro) once it looks right. Try this:

```
Generate a 5-second test video using LTX Video: A slow aerial drone shot over a futuristic city at sunset, neon lights reflecting on glass buildings, cinematic. Save to D:/Videos/test1.mp4
```

Cost: ~$0.10. If you like the result, regenerate with Veo 3.1 or Kling 3 Pro for higher quality.

---

## Available Video Models & Pricing

> **AI video can be pricy** — but it's still dramatically cheaper than hiring a production crew. Always check your prompt, image quality, and model choice before generating.

### Premium Quality

| Model | Price/sec | Best For |
|-------|-----------|----------|
| **Veo 3.1** | $0.20-0.40/s | Highest quality, Google's flagship |
| **Kling 3 Pro** | $0.11-0.20/s | Cinematic, native audio support |

### Balanced Quality

| Model | Price/sec | Best For |
|-------|-----------|----------|
| **Kling 2.5 Turbo** | ~$0.07/s | Speed + quality balance |
| **Kling Omni O1** | Varies | Style-guided generation |
| **Seedance 1.5 Pro** | Varies | Motion + dance |
| **Minimax Hailuo-02** | Varies | Latest Minimax |

### Budget / Fast

| Model | Price/sec | Best For |
|-------|-----------|----------|
| **Veo 3.1 Lite** | Cheaper | Budget Veo option |
| **LTX-2 19B** | Varies | Image-to-video with audio |

### Cost Examples

| What You Generate | Model | Duration | Approx Cost |
|-------------------|-------|----------|-------------|
| Quick test | Kling 2.5 | 5 sec | ~$0.35 |
| Good quality | Kling 3 | 5 sec | ~$0.70 |
| Premium | Veo 3.1 + audio | 8 sec | ~$3.20 |

**Tip:** Test with budget models first. Use premium for the final render.

---

## How to Use It

### Generate Video from Text

```
Generate a 5-second video using Veo 3.1:
"A slow aerial drone shot over a futuristic city at sunset, neon lights reflecting on glass buildings, cinematic, 4K quality"
```

### Generate Video from Image (Best Results)

```
First, generate an image with nano-banano-pro:
"A professional woman standing at a modern podium, tech conference, dramatic stage lighting"

Then animate it with Kling 3 Pro:
"She begins speaking confidently, subtle hand gestures, camera slowly zooms in, audience lights in background"
```

### First + Last Frame (Most Control)

```
1. Generate first frame: "A closed laptop on a minimal desk, morning light"
2. Generate last frame: "Same laptop now open showing a dashboard, coffee cup appeared beside it"
3. Use Veo 3.1 to generate the video transition between these two frames
```

### Full Pipeline (Days 1-5 Combined)

```
Let's create a complete product video:

1. Generate a hero image of my product using nano-banano-pro (Day 1)
2. Animate it into a 5-second video with Kling 3 (Day 4)
3. Check the video quality with ai-video-analyzer (Day 2)
4. Add subtitles and trim with ai-video-editor (Day 3)
5. Generate voiceover and add narration with ai-voice-audio (Day 5)

Save the final video to D:/Videos/product-final.mp4
```

---

## Before You Generate (Checklist)

Run through this **every time** to avoid wasting credits:

- [ ] Is my prompt specific? (motion, camera, mood, duration)
- [ ] Is my input image high quality? (2K minimum for image-to-video)
- [ ] Am I using the right model? (budget for tests, premium for final)
- [ ] Is the duration reasonable? (start with 4-5 seconds)
- [ ] Do I have enough credits? (check https://fal.ai/dashboard/usage-billing/credits)

---

## Prompting Tips

### Describe Motion
"Camera slowly pans left, wind blows through trees, birds fly across frame"

### Specify Camera
"Aerial drone shot", "close-up macro", "handheld documentary style", "smooth dolly zoom"

### Set Duration & Mood
"8 seconds, cinematic, dramatic lighting" or "5 seconds, energetic, social media"

### For Image-to-Video
Describe what **changes** — don't repeat what's already visible. "She turns to face camera, wind catches her hair" not "a woman standing in a field"

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "MCP not connected" | Restart Claude Code after adding the MCP |
| "Authorization failed" | Check your API key at https://fal.ai/dashboard/keys |
| "Insufficient credits" | Add credits at https://fal.ai/dashboard/usage-billing/credits |
| Video looks bad | Check input image quality, make prompt more specific |
| Too expensive | Use Kling 2.5 or Veo 3.1 Lite for tests |

---

## Links

- [fal.ai — Sign Up](https://fal.ai)
- [fal.ai API Keys](https://fal.ai/dashboard/keys)
- [fal.ai Credits](https://fal.ai/dashboard/usage-billing/credits)
- [fal MCP Docs](https://fal.ai/docs/documentation/setting-up/mcp)
- [fal Video Models](https://fal.ai/models?categories=video)
- [Course Page — bestguy.ai](https://bestguy.ai/course/10-days-10-skills)
- [HTML Skill Guide (Hebrew)](https://bestguy.ai/course/guides/day04-video-generation.html)

---

<p align="center">
  <strong>10 Days 10 Skills</strong> — Claude Code Course<br>
  <a href="https://bestguy.ai">bestguy.ai</a> · Guy Aga © 2026
</p>
