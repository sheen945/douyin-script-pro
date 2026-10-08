# douyin-script-pro

> End-to-end Douyin viral script creation + AI video visualization pipeline: multi-model relay (Doubao / DeepSeek drafts, Gemini polish) + creative ignition engine + dual anti-mediocrity gates + a full storyboard / character / image / video prompt production line.

## Overview

douyin-script-pro is a WorkBuddy / Claude Code skill that takes a Douyin (TikTok China) script from "I have no idea what to make" all the way to production-ready AI video generation prompts. The upstream is a script production line (topic → structure → draft → scored iteration → polish → packaged delivery); the downstream is a visualization line (scene visual anchoring → character performance profiles → image asset prompts → video prompts) — 11+1 stages in total.

The problems it solves: a single model writes one genre well and another poorly, output reeks of "AI voice," scripts fail platform review, and content lacks differentiation. The skill counters this with **smart model routing** (emotional/warm content to Doubao 2.0 Pro, knowledge/history/culture to DeepSeek V4 Pro, all polishing to Gemini 3.6 Flash), **six principles from Douyin's official algorithm documentation** (multi-objective scoring / combo goals / handshake model / interest clock / re-review survival / originality & exploration), **two anti-mediocrity gates**, and **three embedded pre-checks** (re-review survival / dramatic action / subtext).

Best suited for: Douyin content creators, short-video directors, people producing videos with AI video tools (e.g. Jimeng), and anyone who wants a systematic methodology for topics and scripts.

## Features

- **Creative ignition engine (Stage 0)**: kicks in when you have no ideas — trend sync (Douyin hot search / social topics) → social tension diagnosis (five quadrants: class / generational / gender / technology / culture) → 12-way ideation (reversal / grafting / amplification / miniaturization, three routes each) → three-dimensional convergence scoring, delivering a Top 3 topic list.
- **Smart draft-model routing**: emotional stories / warm branding / hot topics / challenges / documentary-style → Doubao 2.0 Pro; knowledge / cultural interpretation → DeepSeek V4 Pro; Doubao as fallback when the genre is unclear. Based on a head-to-head model benchmark dated 2026-07-23 (opening hook / internet fluency / emotion / logic / stability).
- **HOOK-X hook matrix + six story structures**: pick 1 primary + 1 backup from 8 hook types (conflict / suspense / counterintuitive / resonance / data shock / identity immersion / contrast / time pressure); six structure templates including ledger-style truth reveal, role swap, emotional container, time-travel narrative, challenge narrative, and raw documentary.
- **Three embedded pre-checks**: Stage 2 "re-review survival pre-check" (conflict must resolve positively; never monetize a specific group's pain) and "dramatic action pre-check" (every scene must be writable as "X wants [goal], but [obstacle]"); Stage 3 "subtext pre-check" (never state emotions outright, never write what can't be filmed, cut all preaching) — methodology adapted from @Shanyin's screenwriting/directing masterclass (MIT license).
- **300-point scoring + iterative optimization**: four scoring dimensions (content quality / algorithm fit / originality / challenge-specific), 240 points to qualify for polishing, max 5 iteration rounds with full detail shown each round.
- **Dual anti-mediocrity gates**: Stage 4 Gate 1 (no interchangeable sentences, a memory anchor in the first 5 seconds, a screenshot-worthy closing line, no filler paragraphs, recognizable persona); Stage 7 Gate 2 (irreplaceability, a "holy cow" moment, thumb-stopping first 3 seconds, no redundant buildup, precise search-keyword targeting).
- **Gemini polish (Stage 6)**: six-dimension structural diagnosis (logic chain / redundancy / support / opening / ending / pacing) + four writing-polish principles (be concrete / weight the focus / talk like a human / restrained formatting); the Claude family is explicitly banned from polishing.
- **Complete delivery package (Stage 7)**: 3 title options with a recommendation, tags, BGM, cover design, view-count estimate, engagement guidance, posting-time advice (aligned with the interest clock), and a comment-section operations plan (3-5 seeded comments, each paired with author reply scripts, aligned with the official handshake model).
- **MVP cold-start protocol**: extract the first 30-45 seconds as a minimal viable test; within 72 hours judge against 7 multi-objective thresholds (completion / likes / comments / shares / saves / follows / profile clicks) with a full feedback loop.
- **Sliceable distribution assets**: cover image plan, 15-second trailer, 30-second highlight cut, quote cards, seeded comments — one script, many distribution surfaces.
- **Downstream visualization line (Stages 8-11, lazy-loaded)**: scene visual anchoring → character performance profiles (consistency profile + 300-500-word master acting profile + locked voice prompts) → image asset prompts (pure Chinese, failure-prevention rules) → video prompts (first-frame lock / spatial blocking / physics / lighting lock); optional Stage 10.5 "shot design" (a duration database built from 551 measured shots).
- **Engineered collaboration mechanics**: model-relay prompt packs (ready-to-paste draft/polish instruction bundles for each model window), project status cards, a rollback protocol (version tagging, never auto-redo downstream), and an authoritative-input confirmation rule.
- **Three run modes**: standard (confirm every stage), quick mode ("fast script" runs the whole pipeline silently and delivers the package), and semi-auto mode (only stops at Stages 1 and 4).

## How It Works / Architecture

- **Skill architecture**: the main `SKILL.md` drives the upstream script pipeline; downstream specialist modules and relay prompts live in `references/` and are lazy-loaded on demand — deliberately keeping the always-on context small (only ~400 characters of "must-pass" content are embedded in the main file).
- **Multi-model relay**: the skill does not call model APIs itself. It assembles "draft instruction packs" and "polish instruction packs" that the user pastes into the Doubao / DeepSeek / Gemini windows, then continues the pipeline with whatever comes back. Semi-auto mode reduces interruptions.
- **Official algorithm alignment**: the six principles come from Douyin's official Trust & Safety documentation (trust.douyin.com / 95152.douyin.com); every creative decision must defer to them.
- **Methodology sources**: @Shanyin screenwriting/directing masterclass (dramatic action / subtext / shot design), prompt-infinity-v3_3 (creative ignition engine), deep-writer-pro (six stages + diagnosis + polish principles), douyin-viral-content (9 elements + 300-point scoring), short-video-script (Douyin adaptation), and the AI STUDIO Yangzi dialogue pack (the four downstream visualization modules + master routing).

## Installation & Usage

### Install the skill

Copy this repository into your skills directory, keeping the folder name `douyin-script-pro`:

```bash
# WorkBuddy / CodeBuddy (user-level)
cp -r douyin-script-pro ~/.workbuddy/skills/

# or Claude Code
cp -r douyin-script-pro ~/.claude/skills/
```

For project-level use, copy it into the project's `.workbuddy/skills/` directory. Restart the session and the trigger phrases will match automatically.

### Trigger phrases

| You say | What happens |
|---------|--------------|
| "写抖音脚本" (write a Douyin script) | Standard pipeline (starts at Stage 1) |
| "没想法 / 帮我想选题" (no ideas / suggest topics) | Starts from Stage 0 creative ignition |
| "快速出脚本" (fast script) | Quick mode — no intermediate output |
| "半自动 / 少打断我" (semi-auto / fewer interruptions) | Semi-auto mode — confirms only at Stages 1 & 4 |
| "把脚本做成视频提示词 / 影像化" | Downstream visualization pipeline (Stages 8-11) |
| "从XX阶段继续 / 只做XX" | Relay mode — jumps to the named stage |

### Full pipeline

```
[Upstream: script production line]
Stage 0   Creative ignition (trend sync → tension diagnosis → 12-way ideation → scoring)
Stage 1   Topic analysis + Brief + primary behavior signal + model routing
Stage 2   HOOK-X hooks + story structure + storyboard outline
          (re-review survival pre-check + dramatic action pre-check)
Stage 3   Draft filling + 9 virality elements + compliance review (subtext pre-check)
Stage 4   10-item self-check + 300-point scoring + Anti-Mediocrity Gate 1
Stage 5   Iterative optimization (max 5 rounds, 240 points to pass)

[Switch → Gemini 3.6 Flash]
Stage 6   Polish (six-dimension diagnosis + four principles)
Stage 7   Packaging + Anti-Mediocrity Gate 2 + MVP cold start + sliceable assets

[Downstream: visualization line (lazy-loaded from references/)]
Stage 8   Scene visual anchoring
Stage 9   Character performance profiles
Stage 10  Image asset prompts
Stage 10.5 Shot design (optional — only for fine-grained storyboards)
Stage 11  Video prompts
```

## Project Structure

```
douyin-script-pro/
├── SKILL.md                        # Main skill file: upstream pipeline + six principles + hard rules
├── README.md                       # Detailed Chinese README
├── README_EN.md                    # This file (detailed English README)
└── references/                     # Lazy-loaded modules, kept out of the standing context
    ├── 00-模型接力提示词.md         # Model-relay prompt pack templates (v5.2)
    ├── 08-分场视觉锚定.md           # Stage 8 module
    ├── 09-角色表演档案.md           # Stage 9 module
    ├── 10-图像资产提示词.md         # Stage 10 module
    ├── 11-视频提示词.md             # Stage 11 module
    ├── 12-镜头设计.md               # Stage 10.5 module (551-shot duration database)
    └── 更新日志.md                  # Full changelog since v3.0 (historical document)
```

## Notes & Caveats

- **Model availability dependency**: the routing scheme is based on a 2026-07-23 benchmark (Doubao 2.0 Pro / DeepSeek V4 Pro / Gemini 3.6 Flash); re-benchmark when models are superseded. The Claude family (Opus 4.6/4.7/4.8/Fable 5) is explicitly deprecated — do not use it for polishing.
- **Manual relay required**: drafts and polishing are executed by the user pasting instruction packs into the respective model windows — the skill does not call APIs itself, so the pipeline stalls without access to those models.
- **Compliance hard rules**: no superlative claims, no named state institutions, no real celebrities (unless deceased 50+ years), no medical-efficacy claims, no politically or religiously sensitive content — enforced throughout, plus a dedicated compliance gate before any downstream prompt output.
- **Lazy-loading discipline**: load only one references/ module at a time and finish it before loading the next, so screenwriting rules and cinematography rules never contaminate each other; script-only sessions never touch the downstream.
- **Rollback protocol**: when an upstream problem surfaces downstream, return to that stage and fix only the specified issue; tag versions, keep old ones, and never auto-redo downstream work.
- **Authoritative-input confirmation**: user-uploaded scripts / character cards / asset images become authoritative only after the user explicitly says "treat these as authoritative."

## License

MIT (the @Shanyin screenwriting/directing methodology included is also MIT-licensed)

## Author

sheen945
