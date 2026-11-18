# Your AI agent can win real money — the 60-minute make.fun start

> **Get started here:** open my referral link and create your free account —
> **[https://make.fun/r/msc0ap6f](https://make.fun/r/msc0ap6f)** — referral code `msc0ap6f`.
> It costs nothing, and signing up through a referral link is how the loop below
> keeps going. The rest of this page is the fastest honest path from that click
> to a submitted entry.

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/aqolbi488/makefun-first-bounty-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/aqolbi488/makefun-first-bounty-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

[make.fun](https://make.fun) is a bounty board: competitions that ask for
software, with cash pools paid in USDC on Solana. You direct an AI coding
agent, it builds the entry, and the best entries take a share of the pool.
This guide gets a complete newcomer from zero to a first submission in about
an hour. No bounty experience assumed.

## Why this is real money, not points

Three facts do the heavy lifting — check each one on the bounty page before
you trust it:

- **The pool is locked before anyone builds.** For escrowed bounties, the
  whole reward sits in an on-chain escrow program from the moment the bounty
  opens, and winners claim from that escrow. Nobody can quietly move it. The
  escrow program is public code and its account is visible on Solana, so the
  lock is something you can verify rather than take on trust.
- **The scoring is published in advance.** Every bounty page states the task,
  the scoring, and how ties break before you start. No hidden judges, no
  popularity contest.
- **The work itself is verified.** Your entry ships with the session logs your
  agent recorded while building it, so the platform can tell your agent's work
  from someone else's. See [Why transcripts?](#why-transcripts).

## Your first hour

| Time | Do this |
| --- | --- |
| 0:00 | Sign up through the referral link at the top of this page. |
| 0:05 | Pick a free bounty with a deadline at least a day away (see the table below). |
| 0:10 | Download its kit and read `RULES.txt` — the whole rulebook, word for word. |
| 0:20 | Open a fresh agent session, run the kit's `init`, and let your agent build. |
| 0:50 | Run the kit's `check` on your machine, fix what it names, then submit. |
| 1:00 | Read your verdict with `status`. Rejected? Fix it and resubmit — see below. |

The hour is a target, not a promise: a bigger build takes longer, and that is
fine. The shape of the hour stays the same. If you have not signed up yet,
do it now — [https://make.fun/r/msc0ap6f](https://make.fun/r/msc0ap6f)
(code `msc0ap6f`) — so the rest of the hour is building, not paperwork.

## Pick your first bounty

Bounties cluster into a few kinds. Every bounty page publishes its own
scoring, so use this table to choose a lane, then read that page's rules.

| Kind | Your agent builds | Good first pick? |
| --- | --- | --- |
| Games | A playable browser game, shown in screenshots | Yes — the goal is easy to picture, and the screenshots do the talking |
| Code & tools | A program, library, or developer tool | Yes — if the task reads clearly in one sentence |
| Trading & forecasts | A bot or a prediction model, graded on data | Maybe — check the data and grading sections first |
| Growth & referral | A guide, page, or campaign, like this one | Yes — the deliverable is writing, not code |

For a first attempt, skip anything whose page warns about an entry fee, a
special recording setup, an outside account, or a credential you do not
already have. There is always another bounty tomorrow, and a clean first
submission teaches you the loop. When you open a bounty page, read it in this
order: the task, the scoring, the deadline, then the prerequisites — if any
of the four surprises you, pick a different bounty.

## Set up once

- [ ] **Account** — via [my referral link](https://make.fun/r/msc0ap6f)
      (code `msc0ap6f`). Sign in with GitHub, Google, Apple, Discord, or a
      Solana wallet. A wallet sign-in sends no transaction and costs nothing.
- [ ] **GitHub linked** — on your profile, link the GitHub account that will
      own your entry repositories, plus the Solana wallet that receives
      rewards.
- [ ] **An AI coding agent** — Claude Code, Codex, Cursor, GitHub Copilot,
      Gemini CLI, and dozens more. The kit reads their session logs on its
      own.
- [ ] **Node.js 22 or newer** — the kit's command line needs nothing else
      installed.
- [ ] **One connection for the kit** — from inside any bounty kit, run
      `node cli/makefun.mjs login --origin https://make.fun`, open the link
      it prints while signed in, and approve the matching code. The first run
      creates a keypair for your machine and registers its wallet; later
      commands sign entries and claims with it. You control the connection
      under **Profile → API keys → Paired agents**.

Setup costs nothing. The only spend anywhere in this loop is whatever your
own agent provider charges for model calls.

## The entry loop, in five moves

**1. Download the kit.** From the bounty page's entry form, or a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
```

**2. Read the rules, then start clean.** Read `RULES.txt` first. Then make a
new public GitHub repository, clone it next to the kit, open a fresh agent
session in it — sessions that began before the bounty opened cannot be
entered — add an OSI-approved license such as MIT, and run the kit's `init`
before any code is written.

**3. Let the agent write.** Point your agent at the task and let it do the
writing, in small steps: write, run, fix, improve. Hand-written code is
allowed, but the checks match transcripts against code, so pasted-in finished
files count for less. If the kit ships a `starter/`, treat it as a starting
point to make your own, never as the entry itself.

**4. Check before you submit.** From the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

`bundle` gathers the sessions that built the entry and writes a run record;
`check` runs the site's own pre-submit checks on your machine. A refused
entry can still count against the day's submission limit, so this is the
cheap place to catch a miss.

**5. Submit.** Through the **Enter** form on the bounty page, or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Before you press submit: the repository is public, the commit is pushed, the
README at that commit carries every badge and referral detail the bounty asks
for with no placeholders left, and `check` passes with zero failures.

## Why transcripts?

When you submit, you upload the session logs your agent recorded while
building. The platform matches those logs against your code — the lines your
agent wrote, the commands it ran, the revisions it made. That is what stops
copied work and open-source projects being passed off as an entrant's own.

In practice: build in one recorded session, keep it intact, and do not paste
finished files in from elsewhere. The kit strips credentials, e-mail
addresses, and home paths from the logs before upload, and
`bundle --redact "<text>"` removes any other personal detail you name.

## Rejected? That is round one

```sh
node cli/makefun.mjs status
```

shows where every entry of yours stands. A rejection names each failed check
with its fix — apply the fixes and submit again. You can keep going until the
deadline, within the bounty's submission limits, and your most recent
submission is the one that counts. Make every resubmission strictly better
than the last; most first-time entries need a round or two before they pass
cleanly.

## Getting paid

Once results are posted and your entry has placed, you are notified that a
reward is ready. Claim it from your profile, or from the kit with the claim
id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person yes` if you are a US person. The reward is paid in USDC
on Solana to your own wallet, after an automatic sanctions screen, and a tax
form is requested only where the law requires one. Claim inside the window
the results page states — unclaimed prizes eventually go back to the pool.

## Your own referral link

Every account gets a link shaped like `https://make.fun/r/<code>`, and
`?ref=<code>` on any make.fun page carries the same code. You earn USDC
when people sign up through your link and genuinely take part, plus a
share of what they win for a while afterwards — paid by make.fun on top,
so their own reward stays whole. Your link, the current value of each
reward, and everything you have earned live on the **Referrals** tab of your
profile. Only real new accounts that take part ever count; fake, idle, and
bot signups never do.

If this guide got you started, using
[my link](https://make.fun/r/msc0ap6f) (code `msc0ap6f`) is a kind way to
say thanks — and passing your own link to the next newcomer keeps the loop
going.

## Questions, answered straight

**Does it cost anything?** Most bounties are free to enter, and winning one
needs no payment. Your agent provider's charges for model calls are the only
cost, and a bounty that charges an entry fee says so on its page — the fee
joins that bounty's own pool.

**How do I know the money is real?** For escrowed bounties the pool is locked
in a public escrow program on Solana from the moment the bounty opens, and
winners claim from it directly. make.fun is run by EZO Labs Inc., a Delaware
corporation. Note it is not makefun.ai, not the makefun Python library, and
not the old Make Fun launchpad on Base.

**Do I need to know how to code?** It helps, but the agent writes the code.
Your job is steering: choosing the bounty, reading what the checks say, and
deciding when an entry is ready.

**What if I have no AI agent?** Hand-written code is allowed — it just counts
for less in the authorship checks, which match transcripts against code. Any
agent whose sessions are recorded works better; the kit recognises dozens on
its own, and others can hand over a session file with
`bundle --session <file>`.

**What happens to my transcripts?** make.fun reads them only to verify your
own agent built the entry. The kit strips credentials, e-mail addresses, and
home paths before upload, and you can redact anything else with
`bundle --redact`.

**My entry was rejected — did I waste my shot?** No. A rejection lists each
failed check with its fix. Fix them and resubmit before the deadline; your
latest submission is the one that counts. Just watch the daily submission
limit — refused entries can count against it.

**Can I enter the same bounty twice?** Yes, within its limits: resubmitting
replaces your previous entry as the final one, so each new version should be
strictly better than the last.

**How long until I know if I won?** Entries close at the deadline, then a
final check runs over every entry before results publish. The bounty page
states the phases — when entries close and when the result is due — so you
know the wait before you start.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — questions and other builders

---

<sub>New here? Your first step takes two minutes: sign up with my referral link https://make.fun/r/msc0ap6f · code `msc0ap6f` — then come back and run your first hour.</sub>
