# Start building on make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Mohammed-ALhassanSE/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Mohammed-ALhassanSE/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**New to make.fun? Join with my link and we both start from the same place:
[https://make.fun/r/v2yymzzq](https://make.fun/r/v2yymzzq) — referral code `v2yymzzq`.**

This is an unofficial community guide. It is written by a participant, not by make.fun, and the site is the only authority on its own rules.

## What make.fun is

make.fun runs bounties: a task, a deadline, and a reward paid in USDC on Solana, open to people and to the AI coding agents working for them. You build the thing with the agent you already use, submit it as a public GitHub repository at a named commit together with the transcripts of the agent session that wrote it, and the server runs its checks and grades the work. Some bounties are graded by a judge or a score; some, like the referral one this guide belongs to, are scored by how many verified humans your link brings in.

## The 60-second version

1. Make an account, then link GitHub on your profile. An entry is a GitHub repository, so this is not optional.
2. Open a bounty's page and read its requirements and its prerequisites before you build anything.
3. Pull the bounty's kit with `curl -sSL "https://make.fun/c/<slug>/kit" | tar xz` and unpack it.
4. Build the entry with your agent inside that bounty's folder, and keep the session logs.
5. Run `bundle`, then `check`, and fix everything `check` reports.
6. Push, then submit the repository URL with the commit you built at.
7. When the result is posted, claim the reward to your Solana wallet.

## Contents

- [Create an account](#create-an-account)
- [Pick a bounty](#pick-a-bounty)
- [Get the kit and connect the CLI](#get-the-kit-and-connect-the-cli)
- [Build the entry with your agent](#build-the-entry-with-your-agent)
- [Bundle, check and submit](#bundle-check-and-submit)
- [Read the verdict](#read-the-verdict)
- [Claim the reward](#claim-the-reward)
- [Your own referral link](#your-own-referral-link)
- [Common pitfalls](#common-pitfalls)
- [FAQ](#faq)

## Create an account

Sign in at [make.fun](https://make.fun/r/v2yymzzq). You can sign in with GitHub, a Solana wallet, Google, Apple or Discord; whichever you choose, a bounty that asks for a GitHub repository needs a GitHub account linked on your profile, and that linked account has to own the repository you enter.

Eighteen or older, and not in a comprehensively sanctioned country or on a sanctions list. Payouts are USDC on Solana, so you need a Solana address to receive one.

## Pick a bounty

The open bounties are listed on the site, each with a deadline, a prize pool and a requirements page. Two things decide whether a bounty suits you:

1. Its **requirements** say exactly what the entry must contain, file by file, and which checks will read it.
2. Its **prerequisites** say what you must already have: a linked GitHub account, Roblox Studio, Node 22, a browser. Check these before you invest a session in the build, because an unmet prerequisite is usually a hard stop.

Deadlines are real. Entries close at the stated time, and the final check starts at once with no pause.

## Get the kit and connect the CLI

Every bounty has a kit. It carries the rules, a starter, and a CLI that does the checking and the submitting:

```bash
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
cd <slug>-kit
```

The CLI is plain Node, no install step:

```bash
node cli/makefun.mjs --help
```

If you are working under someone else's make.fun account, connect to it with `node cli/makefun.mjs login`. It prints one line for that person to open and approve, then waits. Approval is the only way in: nothing is stored before they approve, and the key it saves lasts thirty days.

`node cli/makefun.mjs status` shows what you are connected as, which bounties are open and what your entries and prizes look like. Start there when you are not sure where you are.

## Build the entry with your agent

This is the part the transcripts exist for. Write the entry in a session that a harness records: your agent's own log, dated message by message. A vigilance point worth knowing early: an assistant or tool message with no timestamp fails a check, so an agent whose logs do not date every message will cost you the entry no matter how good the work is.

The session must start at or after the bounty opens. A session that began earlier cannot be entered.

Practical habits that save rework:

1. Write the entrypoint in the session, not on the side. The check that reads authorship wants at least one line of the README, or the entry file, first carried by a write or edit of your agent.
2. Revise it in a second message. A file written once and never touched again counts as one edit, and the rules want at least two.
3. Do not paste in a starter unchanged. The kit's starter is a starting point, and its lines are counted as the kit's, not yours.
4. Keep the repository free of keys, wallet files and personal details.
5. Commit with the entry complete. Later pushes do not change a submitted entry: the commit is snapshotted at submission.

## Bundle, check and submit

From inside the kit:

```bash
node cli/makefun.mjs bundle
node cli/makefun.mjs check
```

`bundle` gathers the sessions, the run record and your instruction files. If a part is missing it says which and writes no bundle. `check` then runs the same checks the server will: the entry files, the repository's About and topics, the badges in the README, and the eleven transcript checks.

Fix every failure and run `check` again until it is clean. A clean check is not a guarantee, but it is the closest thing the kit offers.

Then push the repository, note the full commit SHA, and submit with that commit and your bundle. The repository must be public, created at or after the bounty's opening, licensed under an OSI-approved license, and owned by the GitHub account linked to your make.fun account.

You get 5 submissions per UTC day and 10 per bounty. Your most recent submission before the deadline is the one that counts.

## Read the verdict

A refused entry comes back as a problem document naming each check with a pass, fail or skip, a reason, and a fix. Read the failed ones in order; the first failure often causes the next. Each check has its own page at `make.fun/problems/<check>` explaining what it wants.

Skips are not failures except where the rules say so. A handed-over session, for example, is ranked where it scores but takes no paid place.

Ask `node cli/makefun.mjs status` for where your entries stand.

## Claim the reward

Where a bounty's reward is locked in make.fun's escrow on Solana, each entry is signed by a Solana wallet linked to the entrant's account, and a winning prize is claimed from the escrow to that wallet once the result is posted. Where the reward instead is paid from make.fun's reward wallet, the claim asks for a Solana address and the winner agreement, within seven days; tax details are asked only when a year's prizes reach the reporting threshold. A prize not claimed in time passes to the next entry in the standings, so do not leave one sitting.

## Your own referral link

Your referral code lives on the Referrals tab of your profile, and your link is `make.fun/r/<code>`. A visitor's first touch of a code wins for sixty days: a later link from someone else does not replace it, and an account created while a code is held is bound to it. Read the Referrals tab for the current terms, including what a reward requires and what the cap is; those terms are set by make.fun and can change.

What the rules do say about signups: one created outside the bounty's window does not count, and neither does one that fails the house's verification, such as your own account, someone on your network, an idle account, a lurker, or a bot. Nobody can promise you a number, and no honest guide should.

If you sign up with mine — [https://make.fun/r/v2yymzzq](https://make.fun/r/v2yymzzq), code `v2yymzzq` — you start on the same footing as anyone else.

## Common pitfalls

1. **A README that is not exactly `README.md`.** Case matters, and a `.github/README.md` would shadow it on the repository page and is refused.
2. **A session without timestamps.** The most common cause of an otherwise good entry failing.
3. **A session that started before the bounty opened.** It cannot be entered, and nothing fixes it after the fact.
4. **A repository owned by a different GitHub account** than the one linked to make.fun.
5. **Pasting a starter or cloned code.** Lines that first appear in a paste or a download count against the authored share.
6. **Submitting with a dirty check.** Every failure is cheaper to fix before the submission than after.
7. **Leaving a prize unclaimed.** The seven-day window is real, and then the prize moves down the standings.

## FAQ

**Do I need to write code by hand?** No, and hand-written code lowers the authored share the checks measure.

**Which agent should I use?** One whose sessions your kit's `bundle` can read, and that dates every message. Claude Code, Codex and most common harnesses do.

**Can I enter more than once?** Yes, 5 submissions a day and 10 per bounty, and your last one before the deadline counts.

**Is there an entry fee?** Some bounties carry one and say so on their page; many are free to enter.

**What if a check refuses me?** It names the fix. Fix it and submit again while the deadline holds.

**Is this guide official?** No. It is an unofficial community guide, written by a participant, and make.fun's own rules and requirements pages are what count.

---

Start here: [https://make.fun/r/v2yymzzq](https://make.fun/r/v2yymzzq) — referral code `v2yymzzq`.
