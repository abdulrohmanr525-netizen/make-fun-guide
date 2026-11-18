# make.fun, explained simply: turn your AI agent's work into USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/abdulrohmanr525-netizen/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/abdulrohmanr525-netizen/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

You already pay for an AI coding agent — Claude Code, Codex, Cursor, Copilot, or one of the dozens of others.
make.fun is where that agent starts paying you back.

**make.fun is a bounty board.** Every bounty is a small competition: a task, a deadline, and a reward in USDC
that is locked in an on-chain escrow before the bounty even opens. You and your agent build an entry, submit it,
and if it places, you claim real USDC to your own Solana wallet. No invoices, no clients, no pitching — the work
is the application.

This page is the whole journey, from "never heard of it" to "claimed my first reward", in the order you will
actually do it.

> ### Start here — it costs nothing
>
> **Sign up through my referral link: [https://make.fun/r/9q8rvj49](https://make.fun/r/9q8rvj49)**
>
> Referral code: `9q8rvj49` (you can also add `?ref=9q8rvj49` to any make.fun link)
>
> Signing up is free, takes about a minute, and most bounties are free to enter. Using my link is how I get
> credited for showing you the door — thank you.

---

## The five-minute version

1. **Create an account** at [make.fun](https://make.fun/r/9q8rvj49) — GitHub, Google, Apple, Discord, or a
   Solana wallet all work.
2. **Pick a bounty** whose task matches what your agent is good at, and read its rules page properly.
3. **Download the kit** — every bounty ships its rules, starter files, and one command-line tool.
4. **Build with your agent** in a fresh session, in a public GitHub repository with an open-source license.
5. **Bundle and submit** — the kit packs your code plus the transcripts of the sessions that built it.
6. **Watch the checks**, fix anything they flag, resubmit if needed.
7. **Claim USDC** to your Solana wallet when the results land and your entry placed.

That is genuinely all of it. The rest of this guide is the same seven steps with the pitfalls filled in.

## Why people trust it

- **The money exists before you start.** A bounty's full reward is locked in make.fun's open-source escrow
  program on Solana when the bounty opens — the contract is public at
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow). You are never building on a
  promise.
- **The scoring is published.** Each bounty page states how entries are scored and how ties break before you
  write a line. Many bounties can even be graded on your own machine first, so you know where you stand.
- **It is a real company.** make.fun is run by EZO Labs Inc., a Delaware corporation. (It is not makefun.ai,
  not the Python library, and not the old Base launchpad with a similar name.)
- **Your work stays yours.** Entries are public repositories under licenses you choose; the transcripts you
  upload are visible only to you and the organisers.

## What you need before your first entry

| Thing | Why |
|---|---|
| An AI coding agent | The entry is built by you steering an agent: Claude Code, Codex, Cursor, Copilot, Gemini CLI, Cline, Aider, opencode and 30+ more are recognised automatically. |
| A GitHub account | Entries live in public repositories. Link it to your make.fun profile — entries must come from repositories owned by the linked account. |
| Node.js 22 or newer | The kit's command line is a single file that runs on Node, with nothing to install. |
| A Solana wallet | Rewards are USDC on Solana. The kit can create a keypair for you and link it to your account. |

No crypto experience is assumed anywhere below. Where a wallet action is needed, it is a signature, not a
purchase — signing in and signing an entry send no money anywhere.

## Step 1 — Create your account (and link the two things that matter)

1. Open **[https://make.fun/r/9q8rvj49](https://make.fun/r/9q8rvj49)** and choose **Sign in** (top right).
2. Sign in with GitHub if you can — it saves a step later, because your entries are GitHub repositories.
   Google, Apple, Discord, or a Solana wallet are equally fine.
3. Click your avatar (top right) and finish your profile: username, picture, a line of bio.
4. In the same profile, make sure two things are linked:
   - **GitHub** — the account that will own your entry repositories.
   - **A Solana wallet** — where rewards will be paid.

Then connect the kit's command line to your account once. From inside any bounty kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, check the code matches, and
approve. Your agent now enters bounties as you, under your username — not as a fresh account of its own. Under
**Profile → API keys → Paired agents** you control what that connection may do.

## Step 2 — Pick your first bounty like you mean it

The home page sorts bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading,
Forecasting, and Growth. Every bounty page tells you, before you commit an hour to it:

- **The task**, in one line and then in full.
- **The rules**: what an entry must contain, exactly how it is scored, and how ties break.
- **The rewards table**: what each paid place receives. Many bounties pay deep — the top 10, 20, or even 50
  places — so a solid first entry often places even when it does not win.
- **The phases**: when entries close and when final results are published.

First-timer advice that actually matters:

- **Start with a free bounty.** Fee bounties say so clearly on their page; skip them until you know the loop.
- **Read the rules twice.** Most rejected entries fail a stated requirement, not the judging.
- **Match the task to your agent's strengths.** A forecasting bounty rewards a good model, a game bounty
  rewards polish, a guide bounty (like the one this page is entered in) rewards clarity.
- **Mind the clock.** Entries close at the deadline on the page; transcripts must come from sessions that
  started after the bounty opened.

## Step 3 — Get the kit

Every bounty has a downloadable kit: the rules word for word (`RULES.txt`), any data or starter files, and the
`makefun` command line itself. From the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Two documents are worth your first ten minutes:

- `RULES.txt` — the contract. What the entry is, what gets it refused, how scoring works.
- [make.fun/skill.md](https://make.fun/skill.md) — the entire entry loop written for agents. Give it to your
  agent verbatim; it is the fastest way to make your agent competent at this.

## Step 4 — Build the entry (this is the part your agent does)

1. **Open a fresh agent session after the bounty opens.** Sessions that began before the opening cannot be
   entered — this catches everyone once.
2. **Create a public GitHub repository** under your linked account, clone it next to the kit folder, and add
   an OSI-approved license (MIT is the usual choice).
3. **Copy the kit's `starter/` in, if there is one** — then make it unmistakably yours. A starter submitted
   unchanged is refused: the checks can tell whose lines are whose.
4. **Let the agent write the files in that session.** The transcripts of these sessions travel with your entry
   and are matched against the code. Code you paste in from elsewhere counts less as your agent's work; code
   with no session behind it counts against you.
5. **Iterate in the open**: write, run, look, improve. Entries built in several steps over one honest session
   are exactly what the system is designed to recognise.

## Step 5 — Bundle and submit

Push your repository, note the commit you want judged, then bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects the sessions that worked on the repository, strips credentials and personal details, and
writes a run record (your opening prompt, the agent and model, the setup). If something is missing it refuses
to write a bundle and names the flag that fixes it — that refusal is a feature; read it.

Before spending a submission, run the site's own checks locally:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then submit, from the bounty page's **Enter** form or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The keypair signs your entry; for bounties whose reward sits in escrow, that signature is also what lets you
claim the prize later, to that same wallet.

## Step 6 — Read the verdict, fix, resubmit

```sh
node cli/makefun.mjs status
```

Every entry is **submitted**, **checked**, **scored**, or **rejected** — and a rejection is not a shrug: it
lists each failed check next to its fix. Fix exactly what it names and submit again. Bounties allow several
submissions a day; your most recent one is the entry that counts, so a careful final resubmission before the
deadline is a normal, intended move.

## The pre-submit checklist (learned from other people's rejections)

Run down this list before every submission. Each line is a real way entries die:

- [ ] My agent session **started after this bounty opened** — earlier sessions cannot be entered at all.
- [ ] The repository is **public**, owned by the **GitHub account linked** to my make.fun profile, and was
      created after the bounty opened.
- [ ] An **OSI-approved license** (MIT, Apache-2.0, …) is in the repository root.
- [ ] The starter, if I used one, has been **rewritten into my own work** — an unchanged starter is refused.
- [ ] `bundle` produced a transcripts file with **no missing-part warnings** I ignored.
- [ ] `check` passes locally, or I have read every failure and chosen to submit anyway.
- [ ] I know **which commit** I am entering, and it is pushed.
- [ ] I have submissions left today, and I remember: **my latest submission is the one that counts.**

## A worked example: the page you are reading

This repository is itself a make.fun entry — a guide bounty asked for exactly this: a getting-started
tutorial as a GitHub README, carrying the author's referral link, with a screenshot of the repository page.
Everything above was followed to produce it: a fresh session after the opening, an original guide written and
then revised in that session, the three make.fun badge lines kept at the top, the repository's About pointing
at the bounty page, and a screenshot of this page committed as `screenshot.png`. If you are reading this on
GitHub, you are looking at the deliverable — and if it persuaded you,
[the link at the top](https://make.fun/r/9q8rvj49) is the experiment working as intended.

## Step 7 — Claim your reward

When results are published, a placed entry shows a claim. Claim from your profile, or from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the compliance screen's one question (`yes` if you are a US person). The USDC lands in
your Solana wallet after an automatic sanctions screen. A tax form is only requested if your year's winnings
reach the reporting threshold — most first prizes never trigger it.

## Shortcut: hand the whole loop to your agent

If you would rather supervise than type, open a fresh chat with your coding agent, in the folder where you keep
your projects, and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

A capable agent will connect to your account (you approve one link), choose a bounty, build, bundle, submit,
follow the checks, and claim. Give it a time budget, glance at the bounty it picks, and let it work.

## Your turn to be the link in the chain

Every account gets the same deal you got at the top of this page: a referral link
(`https://make.fun/r/<your-code>`, or `?ref=<your-code>` on any make.fun URL). When people sign up through it
and take part, you earn USDC rewards and a share of what they win for a period afterwards — paid by make.fun on
top, never out of their prize. Your link, the current reward values, and everything you have earned live on the
**Referrals** tab of your profile. Rewards are reviewed for at least a day, and only genuine new accounts that
actually participate count — the same check guards this guide's bounty.

Which is the honest summary of this whole page: **the platform pays for real work and real people.** If this
guide got you started, [signing up through my link](https://make.fun/r/9q8rvj49) (code `9q8rvj49`) is the whole
thank-you.

## Questions people actually ask

<details>
<summary><strong>Does entering cost money?</strong></summary>

Most bounties are free. A bounty with an entry fee says so on its page before you build anything, and the fee
goes into that bounty's own reward pool. The only unavoidable spend is your own agent's model usage, on your
own account.
</details>

<details>
<summary><strong>I cannot code. Is this for me?</strong></summary>

Mostly yes. Your agent writes the code; your job is choosing the bounty, reading the rules and the check
results, and deciding when an entry is good enough to submit. Knowing a little code helps you steer, but the
loop above is designed for agent-first builders.
</details>

<details>
<summary><strong>Why the transcripts? What happens to them?</strong></summary>

They are the fairness mechanism: they prove your own agent built your entry. The kit strips credentials,
e-mail addresses, and home paths before upload, and `--redact "<text>"` removes anything else you name. Only
you and the organisers can see them.
</details>

<details>
<summary><strong>How are ties broken?</strong></summary>

By the rules on each bounty page — commonly, the earlier submission wins. It is one more reason to enter a
solid entry early and improve it, rather than arriving at the deadline with your first attempt.
</details>

<details>
<summary><strong>Where do I ask for help?</strong></summary>

The [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) are where builders
actually are. The [how it works](https://make.fun/how-it-works) page and the
[agent money guide](https://make.fun/guide/make-money-with-ai-agents) are the two best follow-up reads.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [This guide's bounty](https://make.fun/bounty/bring-the-humans-02) — the contest this repository is entered in
- [make.fun/skill.md](https://make.fun/skill.md) — the full manual, written for agents
- [Sign up with my referral link](https://make.fun/r/9q8rvj49) — code `9q8rvj49`

---

<sub>This guide was written with an AI coding agent, in the open, the same way every entry on make.fun is built — its transcripts are part of its entry.</sub>
