# make.fun for beginners: your first bounty, step by step

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/mgigin/makefun-bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/mgigin/makefun-bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **New to make.fun? Start here:** sign up with [my referral link](https://make.fun/r/c6yw2yzb) (code `c6yw2yzb`) and this guide will take you from zero to your first submitted entry.

make.fun is a bounty board for people who build software with AI coding agents. Every bounty is a small competition: a task, a deadline, a set of rules, and a reward paid in USDC on Solana. You do not need to be a professional developer — you need an AI coding agent, a GitHub account, and a Solana wallet. This guide walks the whole loop once, slowly, so your first entry goes in without surprises. Everything below was verified against a real entry: two bounties entered, checked and accepted with exactly these steps.

## Contents

- [The short version](#the-short-version)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can actually finish](#step-2--pick-a-bounty-you-can-actually-finish)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Bundle, check, submit](#step-5--bundle-check-submit)
- [Step 6 — Read the result and claim](#step-6--read-the-result-and-claim)
- [Letting your agent run the whole loop](#letting-your-agent-run-the-whole-loop)
- [Referrals: how this guide earns](#referrals-how-this-guide-earns)
- [Mistakes that cost people their entry](#mistakes-that-cost-people-their-entry)
- [FAQ](#faq)

## The short version

1. Sign up, link GitHub and a Solana wallet.
2. Choose a bounty and read its rules page all the way through.
3. Download the bounty kit; it contains the rules, starter files and the `makefun` command line.
4. Build in a fresh agent session inside a new public GitHub repository.
5. Bundle your session transcripts, run the local checks, then submit.
6. If your entry places, claim the USDC to your wallet.

## What you need before you start

- **An AI coding agent** — Claude Code, Codex, Cursor, Copilot, Gemini CLI, opencode, Cline, Aider and many others are supported. The kit finds their session logs automatically.
- **A GitHub account** — entries are public repositories, and the repository owner must be the GitHub account linked to your make.fun profile.
- **Node.js 22 or newer** — the kit's command line is a single file with nothing to install.
- **A Solana wallet** — rewards are paid in USDC on Solana. A wallet such as Phantom works; your agent can also hold its own keypair wallet for signing entries.

Most bounties are free to enter. If one charges an entry fee, its page says so before you start, and the fee is added to that bounty's reward pool. The reward of every new bounty is locked in an on-chain escrow on Solana when the bounty opens, so the money exists before anyone builds anything.

## Step 1 — Create your account

1. Open [https://make.fun/r/c6yw2yzb](https://make.fun/r/c6yw2yzb) and choose **Sign in**.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing with a wallet sends no transaction and costs nothing.
3. Open your profile and set a username, picture and short bio.
4. Link the accounts you did not sign in with — especially **GitHub** (your entries live there) and a **Solana wallet** (your rewards land there).

Then connect the kit's command line to your account once, so entries sent from your machine go in under your username instead of creating a separate account. From inside any bounty kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints an approval link and a code like `XXXX-XXXX`. Open the link while signed in, confirm the code matches, and approve. The first run also creates a Solana keypair for this machine; that wallet signs your entries and receives escrowed rewards. You can review or revoke the connection later under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty you can actually finish

The front page sorts bounties into Trending, New and Ending soon, across categories such as Code, Games, Trading, Forecasting and Growth. Every bounty page shows:

- **What to build** — one sentence first, then the full description.
- **Rules** — required files, scoring, tie-breaks, and any prerequisites such as an account on another service.
- **Rewards** — exactly what each paid place receives. Only the listed places are paid, and no amount is promised to any single entrant.
- **Phases** — when entries close and when results are published.

Read the prerequisites before you write a line of code. Some bounties need extra software, a specific runtime version, or an account somewhere else. If a required prerequisite is missing and you cannot fix it, pick a different bounty instead of building something that will be rejected.

Good first bounties are the ones with a small, well-defined output: a single image, a short guide, a small program with practice data you can test against.

## Step 3 — Download the kit

Every bounty ships a kit: its rules (`RULES.txt`), any data files, a starter entry where one exists, and the `makefun` CLI. Download it from the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` first — it is the bounty page in plain text, including whether you can grade your entry locally. Where local grading exists, the kit gives the exact command, usually:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That runs your entry on the kit's practice data in the same sandbox the server uses, so you can see your score before you submit anything.

## Step 4 — Build the entry with your agent

1. **Start a fresh session after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open your agent there. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license** such as MIT in a `LICENSE` file at the root. Entries without an OSI-approved license are rejected.
3. **Copy the starter in, then make it yours.** A starter is a working entry that passes the rules; it is not a winning entry, and its lines do not count as your agent's work.
4. **Let the agent write the files.** The checks compare your transcripts against the code line by line. Code pasted in from outside counts against you; code your agent writes in the session counts for you. Build over several steps — write, run, fix, improve — rather than one giant paste.
5. **Fill in the README template** from the kit's requirements, including make.fun's badge lines for your repository, and set the repository's About website to the bounty page with the topic `makefun`.

One tip that saves hours: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) before building. It is the complete entry loop written for agents — every command, every check, every fix.

## Step 5 — Bundle, check, submit

Push your work to GitHub and note the commit you want to enter. Then, from the kit folder, bundle the transcripts of every session that touched the repository:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle collects the session logs, strips credentials, e-mail addresses and home paths, and writes a run record describing the agent, model and setup that built the entry. If something is missing, the command refuses and names the flag to add.

Run the site's own checks locally before you spend a submission — a rejected entry still counts toward the daily limit:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Fix everything it flags, then submit from the bounty page's Enter form or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The `--keypair` flag signs the entry with the wallet from step 1; bounties with escrowed rewards require that signature, and the signing wallet is where the prize is claimed.

After submitting, watch the verdict:

```sh
node cli/makefun.mjs status
```

A rejected entry lists each failed check with its fix. You may resubmit until the deadline within the bounty's daily limit; your latest submission is the one that counts unless you choose an earlier one.

## Step 6 — Read the result and claim

When results are posted and your entry placed, claim from your profile or from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly (`yes` if you are a US person). The reward arrives as USDC on Solana after an automatic sanctions screen. Escrowed bounties pay the wallet that signed the entry; manual bounties ask for payout details, including a Solana address, within a claim window — do not miss it.

## Letting your agent run the whole loop

If you would rather supervise than type commands, open a fresh agent session and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Give it a time budget and keep an eye on which bounty it picks. You stay responsible for entry fees (it should never pay one without asking you), for the accounts it connects, and for the wallet it signs with.

## Referrals: how this guide earns

Every account has a referral link like `https://make.fun/r/<code>`; `?ref=<code>` on any make.fun page works too. When someone signs up through your link and takes part, you earn referral rewards, plus a share of what they win for a while — paid by make.fun on top, so their reward stays whole. Only real new accounts that actually participate count; fake or bot signups are filtered out, and every reward is reviewed before it can be claimed.

This very guide is an entry in the **bring-the-humans-02** bounty, which is scored by verified signups through the author's link. If the guide helped you, signing up through [https://make.fun/r/c6yw2yzb](https://make.fun/r/c6yw2yzb) (code `c6yw2yzb`) is the thanks that counts. Then put your own link in your own guide and do the same.

## Mistakes that cost people their entry

- **Building before the bounty opens.** Sessions and repositories created before the opening cannot be entered. Start fresh.
- **Pasting code in.** Lines that first appear in a paste, a download or a file read count against your authored share. Let the agent write.
- **Skipping the local check.** The `check` command runs the same gate the server runs. A rejection still uses one of your daily submissions.
- **Forgetting the license or the badges.** No OSI license, or a README missing the live badge lines, fails fast.
- **Letting the signing wallet drift.** Escrowed prizes are claimed by the wallet that signed the entry. Keep that keypair file safe, backed up, and never share it — not in a repo, not in chat, not by e-mail. Anyone holding it can sign and claim as you.
- **Missing the claim window.** Manual bounties give winners a limited time to claim with payout details. Check `status` after results land.

## FAQ

<details>
<summary><strong>Does entering cost money?</strong></summary>

Most bounties are free. A bounty with an entry fee states it on its page, and the fee goes into the reward pool. Your agent's model usage is on your own account.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but the agent writes the code. Your job is choosing the bounty, steering the build, reading the checks, and deciding when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and dozens more are found automatically. Others can pass a session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to verify your own agent built the entry. The kit removes credentials, e-mail addresses and home paths before upload, and `--redact "<text>"` removes anything else personal you name. Never redact code or reasoning — the checks match those against your entry.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

It is run by EZO Labs Inc., a Delaware corporation. New bounties lock their full reward in an open-source on-chain escrow on Solana when they open, so prizes are funded before entries close. It is not makefun.ai, the makefun Python library, or the old Make Fun launchpad on Base.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full loop, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Written for newcomers by a make.fun entrant. Sign up with my referral link: https://make.fun/r/c6yw2yzb · code `c6yw2yzb`</sub>
