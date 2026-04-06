---
name: fal-ai-video-generation
description: Generate AI videos using fal.ai MCP — text-to-video and image-to-video with Veo 3.1, Kling 3, Kling 2.5, Kling Omni O1, Seedance 1.5 Pro, LTX-2, Minimax Hailuo. Supports first/last frame generation with nano-banano-pro, then video generation, then editing with ai-video-editor and narration with ai-voice-audio. Use when the user wants to generate a video from text or images using AI video models through fal.ai.
allowed-tools: Bash, Read, Write, Glob
---

# fal.ai Video Generation (MCP)

Generate AI videos from text prompts or images using fal.ai's MCP server — access to Veo 3.1, Kling 3, Seedance, LTX, Minimax and more, all from Claude Code.

## What is an MCP?

MCP (Model Context Protocol) is like a plugin for Claude Code. It connects Claude to external services — in this case, fal.ai's 1000+ AI models. Once connected, Claude can generate videos, check pricing, and manage jobs directly.

## Setup

### Step 1: Get a fal.ai API Key

1. Go to [fal.ai](https://fal.ai) and sign up
2. Get your API key at: **https://fal.ai/dashboard/keys**
3. Add credits at: **https://fal.ai/dashboard/usage-billing/credits**

> **Important:** Video generation costs money per second of output. Start with $5-10 in credits to experiment. See pricing table below.

### Step 2: Install the fal MCP (Run in Terminal — NOT inside Claude Code)

**Close Claude Code first.** Then open a regular terminal (PowerShell, Terminal, or Command Prompt) and run:

```bash
claude mcp add --transport http fal-ai https://mcp.fal.ai/mcp --header "Authorization: Bearer YOUR_FAL_KEY"
```

Replace `YOUR_FAL_KEY` with your actual API key from https://fal.ai/dashboard/keys.

> **Why outside Claude Code?** The `claude mcp add` command configures Claude Code itself — it can't configure itself from inside. Think of it like installing a browser extension — you install it from outside the browser.

### Step 3: Restart Claude Code

Close and reopen Claude Code. The fal MCP will load automatically on startup. You should see new fal tools available.

### Step 4: Verify & Install Skill

Now open Claude Code and paste:

```
Install the fal-ai-video-generation skill from https://github.com/guyaga/10d10s-day04-video-generation and verify the fal MCP is connected by searching for available video models.
```

If the MCP is working, Claude will be able to search models, check pricing, and generate videos.

---

## Available Video Models

Always recommend the **latest model** for best results. Here are the key models:

### Tier 1: Best Quality (Premium)

| Model | ID | Type | Price/sec | Best For |
|-------|-----|------|-----------|----------|
| **Veo 3.1** | `fal-ai/veo3.1` | text→video, image→video | ~$0.20-0.40/s | Highest quality, Google's best |
| **Kling 3 Pro** | `fal-ai/kling-video/v3/pro/image-to-video` | image→video | $0.11-0.20/s | Cinematic, native audio, elements |

### Tier 2: Great Quality (Balanced)

| Model | ID | Type | Price/sec | Best For |
|-------|-----|------|-----------|----------|
| **Kling 2.5 Turbo Pro** | `fal-ai/kling-video/v2.5-turbo/pro/image-to-video` | text→video, image→video | ~$0.07/s | Good speed/quality balance |
| **Kling Omni O1** | `fal-ai/kling-video/o3/standard/image-to-video` | image→video | Varies | Style guidance, text-driven |
| **Seedance 1.5 Pro** | `fal-ai/seedance-1.5-pro` | image→video | Varies | Good motion, dance/movement |
| **Minimax Hailuo-02** | `fal-ai/minimax/hailuo-02/standard/image-to-video` | image→video | Varies | Latest Minimax |

### Tier 3: Budget / Fast

| Model | ID | Type | Price/sec | Best For |
|-------|-----|------|-----------|----------|
| **Veo 3.1 Lite** | `fal-ai/veo3.1-lite` | text→video, image→video | Cheaper | Budget Veo |
| **LTX-2 19B** | `fal-ai/ltx-2-19b/image-to-video` | image→video + audio | Varies | Audio from image |

### Pricing Reality Check

> **AI video generation can be expensive** compared to image generation. A single 8-second Veo 3.1 video with audio can cost $3+. However, this is still **dramatically cheaper** than traditional video production (camera crew, actors, editing). Always:
>
> 1. **Check your image quality** before generating — garbage in = garbage out
> 2. **Review your prompt** carefully — be specific about what you want
> 3. **Start with shorter durations** (4-5 seconds) to test before going longer
> 4. **Use budget models first** (Veo 3.1 Lite, Kling 2.5) to iterate, then final render with premium
> 5. **Check your fal.ai credit balance** at https://fal.ai/dashboard/usage-billing/credits

---

## Workflows

### Workflow 1: Text-to-Video (Simplest)

Just describe what you want:
```
Generate a video using Veo 3.1: "A golden retriever running through a sunlit meadow in slow motion, cinematic, shallow depth of field, 8 seconds"
```

### Workflow 2: Image-to-Video (Best Results)

Generate an image first (Day 1), then animate it:
```
1. First, use nano-banano-pro to generate a still frame: "A professional woman presenting at a tech conference, minimalist stage, dramatic lighting"
2. Then use Kling 3 Pro to animate it: "The woman gestures confidently, camera slowly pans right, audience applauds"
```

### Workflow 3: First + Last Frame (Controlled)

Generate both start and end images, then let the AI fill in the motion:
```
1. Generate first frame: "A coffee cup on a desk, morning light, steam rising"
2. Generate last frame: "Same coffee cup, now empty, afternoon light, laptop open behind it"
3. Use Veo 3.1 first-last-frame-to-video to create the transition
```

### Workflow 4: Full Production Pipeline (Days 1-5)

The complete creator workflow:
```
Day 1 (Image): Generate a cinematic first frame for my product video
Day 5 (Video): Animate that frame into a 5-second video with Kling 3
Day 2 (Analyze): Check the generated video for quality issues
Day 3 (Edit): Trim, add subtitles, resize for Instagram Reels
Day 4 (Audio): Generate voiceover narration and add to the final video
```

---

## Prompting Tips for Video Generation

### Be Specific About Motion
- Bad: "A city at night"
- Good: "A slow aerial drone shot gliding over a city skyline at night, neon lights reflecting on wet streets, camera tilts down gradually, cinematic"

### Describe Camera Movement
- "Camera slowly pans left to right"
- "Smooth dolly zoom into the subject's face"
- "Aerial drone shot rising from ground level"
- "Handheld shaky cam, documentary style"

### Specify Duration and Mood
- "8 seconds, cinematic, dramatic lighting"
- "5 seconds, fast-paced, energetic, social media style"
- "6 seconds, slow motion, dreamy, soft focus"

### For Image-to-Video
- Describe what **changes** from the still image
- "The wind blows through her hair, she turns to face the camera"
- "The product rotates slowly on a turntable, studio lighting"
- Don't repeat what's already visible in the image

---

## Quality Checklist (Before Generating)

Run through this before every generation to avoid wasting credits:

- [ ] **Prompt is specific** — describes motion, camera, mood, duration
- [ ] **Image quality is high** (if using image-to-video) — at least 2K
- [ ] **Model matches the need** — don't use $0.40/s Veo for a test
- [ ] **Duration is reasonable** — start with 4-5 seconds for tests
- [ ] **Credits are sufficient** — check balance at fal.ai dashboard

---

## Best Practices

1. **Always use the latest model version** — they improve fast
2. **Generate your first frame with nano-banano-pro** for best image-to-video results
3. **Test with budget models first**, render final with premium
4. **Keep prompts under 200 words** — focused and specific
5. **Check generated video with ai-video-analyzer** if quality is unclear
6. **Edit with ai-video-editor** after generation — trim, add subtitles, resize
7. **Add narration with ai-voice-audio** for the final touch
8. **Monitor your spending** — set a budget and check after each generation
