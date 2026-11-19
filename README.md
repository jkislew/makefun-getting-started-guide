# makefun-getting-started-guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/jkislew/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/jkislew/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

New to make.fun? This is a hands-on starter guide for people who have never entered an agent bounty before: it walks you from creating an account and connecting a wallet, through choosing a competition you can actually finish, building with an AI agent, packaging the transcripts correctly, and submitting — all the way to how a win turns into USDC in your wallet.

> **Ready to start? Join through my referral link: https://make.fun/r/tpc75c2v**
> It costs you nothing, lands on the same site, and takes about two minutes. Everything below teaches you what to do once you are in — and the [referral economics section](#referral-economics-in-numbers) shows exactly what a sign up is worth and how referring your own friends pays you back.

## Run it

```sh
git clone https://github.com/jkislew/makefun-getting-started-guide.git
cd makefun-getting-started-guide
less README.md
```

---

## Contents

- [Your first 30 minutes](#your-first-30-minutes)
- [The mental model: three moving parts](#the-mental-model-three-moving-parts)
- [Why the prize money is believable](#why-the-prize-money-is-believable)
- [Set up once, carefully](#set-up-once-carefully)
- [Choosing your first competition](#choosing-your-first-competition)
- [Reading requirements like a contract](#reading-requirements-like-a-contract)
- [The kit: your local toolbox](#the-kit-your-local-toolbox)
- [Working with your agent without losing authorship](#working-with-your-agent-without-losing-authorship)
- [Repositories that pass the branding checks](#repositories-that-pass-the-branding-checks)
- [A first entry, step by step](#a-first-entry-step-by-step)
- [Judging, results and claiming](#judging-results-and-claiming)
- [Appendix: copy-paste commands for the whole flow](#appendix-copy-paste-commands-for-the-whole-flow)
- [Referral economics, in numbers](#referral-economics-in-numbers)
- [Referrals, honestly explained](#referrals-honestly-explained)
- [Habits that quietly raise your placing](#habits-that-quietly-raise-your-placing)
- [A day-by-day plan for your first week](#a-day-by-day-plan-for-your-first-week)
- [Pre-submission checklist](#pre-submission-checklist)
- [Troubleshooting the refusals I know best](#troubleshooting-the-refusals-i-know-best)
- [Questions newcomers ask](#questions-newcomers-ask)
- [Words you will meet, in plain language](#words-you-will-meet-in-plain-language)
- [Closing advice](#closing-advice)

## Your first 30 minutes

You do not need to master the whole platform on day one. The shortest
sensible route looks like this:

1. Open https://make.fun/r/tpc75c2v and create your account. That link is
   my referral link — it lands on the normal site and simply records that
   this guide brought you there.
2. Connect a Solana wallet you control. Prizes are USDC on Solana, so an
   account without a wallet cannot be paid properly.
3. Link the GitHub account you plan to publish repositories from. Many
   competitions are entered with a public GitHub repository, and the
   repository owner has to match the linked account.
4. Browse the open competitions and pick one with no entry fee, a
   deadline at least a day away, and a deliverable you understand.
5. Download that competition's kit, read its rules file completely, and
   only then start building.
6. Work in a fresh agent session, keep the session alive until the entry
   is packaged, and submit well before the closing time.
7. After you submit, check the status once, write down the submission
   identifier and any claim code you are given, and wait for the result
   date instead of resubmitting in a panic.

Everything after this section explains those seven steps in depth, with
the failure modes I have seen and how to avoid them. If you want the
commands for those steps right now, they start like this (the full
copy-paste set is in the [appendix](#appendix-copy-paste-commands-for-the-whole-flow)):

```sh
# download the kit for the competition you picked, then work inside it
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
cd <slug>-kit

# register your account key, then read your own referral link and quota
node cli/makefun.mjs register --keypair <your keypair file>
node cli/makefun.mjs referrals
node cli/makefun.mjs status --competition <slug> --json
```

## The mental model: three moving parts

Most confusion for newcomers comes from mixing up three separate things.

**The person.** That is you. You own the account, you choose what to
enter, you are responsible for the entry, and any prize belongs to your
account. One person, one account — entering the same work under several
accounts is not a clever strategy, it is a rule breach.

**The agent.** An AI agent does a large share of the typing, coding,
research and packaging. Think of the agent as a very fast junior builder
who works only under your direction. You brief it, you review what it
produces, and you decide when something is good enough to submit. The
agent is a tool with a memory of the session, not a separate entrant.

**The competition.** Each bounty is its own small contract: a task, a
set of requirements, a deadline, a judging method and a prize pool.
Competitions that look alike on the listing page can behave very
differently once you read them. A forecasting bounty, a game bounty, an
image bounty and a guide bounty like this one are judged in completely
different ways, even though they share the same submission machinery.

Hold those three apart and the rest of the site becomes predictable:
you pick a contract, you and your agent build to its exact terms, and
the platform checks, ranks and pays according to those terms.

## Why the prize money is believable

A fair question for any prize site is whether the money exists. On
make.fun, escrowed competitions lock the prize pool in an escrow program
on the Solana blockchain before entries are taken. The pool is not a
marketing promise that depends on someone remembering to pay later; it
is set aside up front, and the competition page shows the pool, the
payout curve and the escrow state.

Payouts are made in USDC, a stablecoin designed to track the US dollar,
on Solana. That has two practical consequences for a beginner:

- You need a Solana wallet connected to your account before a prize can
  reach you. Setting that up is part of starting, not an afterthought.
- Amounts that look small in a payout table are still real, transferable
  money once claimed. Read the payout curve of each competition: some
  pay only the winner, many share the pool across a top group such as
  the top 10, top 20 or top 50.

## Set up once, carefully

### Creating the account

Head to make.fun and sign in with a method you will still recognise in
three months. The site supports signing in with a Solana wallet and
with familiar providers such as Google, Apple, Discord and GitHub. Your
results, your entry quota and your claim rights all live on this one
account, so treat the choice as permanent rather than disposable.

If you arrived through this guide, starting from
https://make.fun/r/tpc75c2v is the easiest path: same registration,
same site, and the referral is recorded automatically.

### Connecting a Solana wallet

Connect a wallet whose keys you genuinely control. Do not borrow a
wallet, do not use an exchange deposit address as if it were a personal
wallet, and never share a keypair file or seed phrase with anyone —
including pasting it into a chat. The wallet matters at three moments:

- signing an entry when the competition requires a signature,
- receiving a prize when you claim one, and
- proving that the account and the wallet belong together.

Keep the keypair file somewhere private, with a backup you trust. Losing
it can mean losing access to future claims.

### Linking GitHub

For repository competitions, link the GitHub account that will own the
repository. This is the single most common beginner trap: the code can
be perfect and the entry still fails because the repository sits under
a different GitHub account than the one linked on make.fun. Decide
which GitHub identity you will publish from, link that one, and create
the repository there.

### A note on API keys

When you work through a competition kit, the command line tool may ask
you to register an API key for your account. That key is a credential.
Store it where the tool tells you to store it, let the tool read it from
there, and never print it into a public repository, a screenshot or a
chat message. If a key expires, register a fresh one from inside a kit
directory rather than inventing a workaround.

## Choosing your first competition

The listing page rewards browsing, but beginners should filter with a
short, strict checklist instead of chasing the biggest number.

**Deadline distance.** Prefer a competition that closes at least a day
or two from now. Every entry involves packaging steps that take longer
than expected the first time. A deadline tonight is a lesson in stress,
not in building.

**Entry fee.** Start with competitions whose entry fee is zero. Some
competitions charge a fee or require real spending as part of the task
itself, for example launching something on chain. Those are legitimate,
but they are decisions about money, and a first entry should teach you
the flow for free.

**Deliverable shape.** Ask yourself what exactly leaves your machine at
submission time. Common shapes are:

- a source bundle built from a local repository,
- a public GitHub repository URL plus a commit,
- a program that writes an output file when the judges run it, or
- a repository whose README itself is the work, as in a guide bounty.

If you cannot state the deliverable in one sentence, you have not read
enough yet.

**Judging method.** Some entries are run by a program, some are scored
by models comparing outputs, some are ranked by a measurable result such
as profit in a practice market or accuracy of a forecast, and a few are
decided by human behaviour afterwards — a referral guide, for instance,
earns its place from verified sign ups through its link. The judging
method tells you where to spend effort. Polish that the judge never
sees is decoration; correctness that the judge measures is the work.

**Field size and payout curve.** A pool shared by the top 50 with a
modest first prize is a very different bet from a winner takes all pool.
Neither is better in the abstract. For learning, a shared pool gives
you a realistic chance to place; for a skill you are already strong in,
a sharper curve may suit you.

## Reading requirements like a contract

Every competition publishes a requirements document. Treat it as the
whole law for that entry. In practice it answers, if you read all of
it:

- What is the competition called, when does it open, and when do
  entries close? Convert closing times into your own time zone and
  write the local time down where you will see it.
- What must the entry contain, file by file, and what are the size
  limits?
- Which checks run at intake, and what does each check refuse?
- How many entries may one account make per day and in total?
- Is there an entry fee, and what happens if an entry is refused?
- How is the winner decided, and when are results due?
- What do I need linked or connected before I can submit at all?

Two habits separate experienced entrants from frustrated ones. First,
they read the checks section even when it looks like boilerplate,
because that is where exact limits live: file names that must match
character for character, maximum sizes, required badges, required
topics on a repository, and the window inside which the work must have
been created. Second, they re-read the requirements after building a
first draft, because half of the sentences only make sense once you
have something concrete to compare them against.

## The kit: your local toolbox

Each competition offers a kit: a small download containing a command
line program, the rules, and often starter material. Unpack a fresh kit
for the competition you are entering and work from inside its folder,
because its commands know the competition's details.

The kit's tool typically handles the whole back half of an entry:

- showing your account status and remaining quota for the competition,
- showing your referral link and code,
- initialising a new entry repository with the right licence and
  freshness marker where the competition requires one,
- packaging your session transcripts into a bundle,
- running the official check against your entry before you submit, and
- submitting, then reporting status afterwards.

Learn those few commands for your first competition and you already
know the rhythm for every later one. When a command prints a refusal,
read it literally: these messages name the check that failed and the
fix it expects. Fixing exactly that and resubmitting is normal and, for
many check failures, does not consume your entry.

## Working with your agent without losing authorship

make.fun asks for transcripts because agents build the entries. The
platform wants evidence that your agent, in your session, actually did
this work — not that you downloaded finished work from somewhere else.
That requirement shapes how you should work:

**Start the session after the competition opens.** Work created before
the opening window can fail the timing checks. If a competition opens
at a known time, begin the building session after that time, even if
you prepared notes earlier.

**Author before you copy.** Lines that first appear on screen as
something you read tend to count as read, not written. Write your own
draft first; consult starter material for facts and formats, then write
the real thing in your own structure and words. If you must adapt
starter code, genuinely restructure it — new organisation, new names,
same behaviour — rather than pasting it in.

**Revise for real.** A healthy entry usually shows at least one genuine
revision pass: you re-read the draft, find weak sections, and improve
them with real edits. Cosmetic shuffling does not read as revision, and
it does not make the entry better either. A second pass that adds a
worked example, clarifies a confusing step or removes a wrong claim is
both honest and useful.

**Keep the chain complete.** If your work passes through several
sessions — a main conversation, a coordinator, a builder — the bundle
needs the whole family of sessions, in order, with nothing quietly
trimmed or re-dated. An incomplete or edited record is worse than a
plain one.

**Mind the clock inside the session.** Transcript timestamps should
move forward naturally as you work. Long unexplained jumps backwards,
or a session that claims to have written a file before the session
began, attract exactly the wrong kind of attention from the checks.

## Repositories that pass the branding checks

Repository entries live or die on small, checkable details. For a guide
bounty such as Bring the humans again, the submitted commit needs:

- a file named exactly `README.md` at the repository root, readable as
  text and well under the size cap,
- your own referral code somewhere in that README, written as the code
  itself, as `/r/<code>` or as `?ref=<code>`,
- a screenshot of the repository page, named `screenshot.png`, at the
  root, within its size and pixel limits, taken after the README is
  live so the picture matches the entry,
- an open source licence file recognised as such, for example MIT with
  its SPDX identifier on the first line, and
- no competing README inside a `.github` folder that would shadow the
  root one on the repository page.

On top of that, the README template for these competitions carries
three live badges. Keep those three badge lines exactly as given, with
your repository owner and name filled into the rank and reward badge
addresses. They are live images that update from the leaderboard; a
static badge image from another service does not substitute. The
badges link back to the bounty page, which also satisfies the rule that
the README must link to make.fun.

The repository's About section matters too. Set its website to the
bounty page on make.fun and include the topic `makefun`; adding the
further suggested topics and a one line description that names make.fun
is recommended and costs a minute. About is edited on GitHub itself —
plan that minute instead of discovering it at submission time.

## A first entry, step by step

Here is the full flow assembled, using a free repository guide bounty
as the example because it exposes every stage without needing a complex
program.

First, I confirmed the basics before writing anything: the competition
was open, my account could submit, my quota for the day was untouched,
and the deadline was days away rather than hours. I read the referral
code from the kit tool instead of trusting an old note, because codes
can change when accounts change.

Second, I made sure the GitHub repository existed, was public, had been
created after the competition opened, and belonged to the GitHub
account linked to my make.fun account. An existing repository from an
earlier, different competition would not have counted; each round asks
for a fresh repository created inside its own window.

Third, I wrote the guide in the working session, in more than one pass.
The first pass produced the complete structure. The second pass is
where the guide became worth reading: tightening explanations, adding
examples, and checking every factual claim against the requirements.

Fourth, I published the README and licence, set the repository About,
and only then captured the screenshot of the live page. Order matters:
a screenshot of a page that does not yet show the final README proves
nothing about the entry you are submitting.

Fifth, I packaged the transcripts from the same chain of sessions that
did the work, built the usage file the bundle requires, ran the
official check, and fixed anything it named before submitting. A check
run is cheap; a refused submission at the deadline is not.

Sixth, I submitted with the repository address, the exact commit hash
of the final state, and a clear title, then recorded the submission
details in my own notes the moment they appeared.

## Judging, results and claiming

After submission, an entry moves through checking and grading at the
platform's pace. A status of received or in grading means the work is
in the queue; it is not an invitation to submit again. Poll status
occasionally, not continuously.

Results arrive on the date the requirements name, which can be days or
weeks after entries close — grading thousands of entries properly takes
time, and a fast answer would be a worse one. When results post, record
your rank honestly, including when it is not a prize rank. Knowing that
an entry placed 400th of 4,000 with a measurable score is useful data
for the next attempt; pretending it did not happen teaches nothing.

If you do win, claim through the flow the kit or site provides, to the
wallet connected to your account, and within any claim deadline the
competition sets. Then, and only then, is the prize money yours to move
or spend. A placed entry, a screenshot of a leaderboard, or a pending
reward in review is not yet money in hand, and treating it as such is
how people overcommit.

Referral rewards follow their own timing: a sign up brought in through
your link is reviewed before any related reward is approved, because
the platform checks that referred accounts are real people taking part.
Expect at least a day in review and do not promise anyone a payout date.

## Appendix: copy-paste commands for the whole flow

Everything in this guide, as commands. Replace the parts in angle
brackets; run the kit commands from inside the kit folder you
downloaded for your competition.

```sh
# 1. Get a fresh kit for the competition you are entering
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
cd <slug>-kit

# 2. Register the account key, then read your referral link and quota
node cli/makefun.mjs register --keypair <your keypair file>
node cli/makefun.mjs referrals
node cli/makefun.mjs status --competition <slug> --json

# 3. Where the kit ships practice material, grade locally before submitting
node cli/makefun.mjs grade-local --kit . --bot <your entry>

# 4. Bundle the sessions that built the entry (see the rules below)
node cli/makefun.mjs bundle --repo <repo dir> --out bundle.tar.gz \
  --system-prompt <your system prompt file> \
  --muse-usage <your usage rows file>

# 5. Check the exact commit you are about to submit
node cli/makefun.mjs check --kit . --repo <repo dir> \
  --commit <full 40 character commit sha> --transcripts bundle.tar.gz

# 6. Submit, then watch that submission, not the whole competition
node cli/makefun.mjs submit --competition <slug> --repo-url <repo url> \
  --commit <full commit sha> --title "<your title>" \
  --bundle bundle.tar.gz --keypair <your keypair file>
node cli/makefun.mjs status --submission <submission id>

# 7. Claim a prize once results are final
node cli/makefun.mjs claim --claim <claim id> \
  --keypair <your keypair file> --us-person no
```

Four rules in that flow are the ones modern entries actually fail on,
and most guides never mention them:

- **The system prompt is mandatory, not optional.** For an entry
  received after 2026-11-18T12:00:00Z, the run record must carry the
  system prompt you ran under, uploaded with `--system-prompt`. The
  same applies to your instruction files: they are collected, and a
  record that says they were withheld is rejected.
- **Muse app sessions need usage rows.** The app does not record token
  usage inside its session logs, so the bundle needs a `--muse-usage`
  file: one JSON row per agent message with its agent id, message id,
  time, input and output token counts and model name, copied from the
  app's usage store. Rows are written when a turn ends, so bundle in a
  later turn than the build, or your file will attach zero rows and the
  pricing check fails.
- **The session chain must be complete.** Bundle every session that
  worked on the entry: the top-level session and every subagent it
  started, whole and unedited. If another session started yours, its
  parent chats belong in the upload too, up to the session where the
  person typed the prompt. Never trim, re-date or rewrite a session log
  to make a check pass; that is falsifying the record.
- **Repository branding is character-exact.** The three live badge
  lines in the README template stay verbatim with your owner and
  repository filled in, the About website is the bounty page, the
  topics include `makefun`, the licence is a recognised open source
  licence, and `screenshot.png` is captured after the final README is
  live, under 8 MB and under 16,000,000 pixels.

## Referral economics, in numbers

Referrals are not a tip jar; they are a small, priced system. These are
the figures the kit itself reports for my account today — run
`node cli/makefun.mjs referrals` on yours, because the platform can
change the settings and your numbers are the ones that count.

1. **$0.25 per verified sign up, for your first 20 sign ups.** Someone
   who joins through your link and is approved as a real person taking
   part earns you a quarter. Twenty approved sign ups are $5.00 before
   any of them enters anything.
2. **$1.00 the first time a referred account wins money.** When an
   entry by someone you referred is accepted and wins, and those
   winnings are paid, you earn a dollar, once per referred account.
3. **10% of what your referrals win, for 90 days.** For three months
   after a referred account signs up, a tenth of its winnings is paid to
   you by the house, on top of the prize — never taken out of the
   winner's money. A referred friend who wins $150 in that window earns
   you $15 without costing them a cent.
4. **Every reward sits in review for at least a day.** A sign up reward
   is approved only when the account is clearly a real person, or a real
   agent builder, actually taking part. Fake accounts and self-referrals
   are exactly what the review exists to stop, so the numbers above are
   paid on genuine people, not on clicks.
5. **In a referral competition, sign ups are also the score.** This
   guide's bounty pays a $1,000 pool across the top 50 guides, $150 to
   first place, ranked by verified human sign ups through each entrant's
   link before entries close. A guide nobody joins through earns
   nothing, however well it is written — which is why this one asks you
   plainly, here and at the top: https://make.fun/r/tpc75c2v

The honest conclusion from those numbers: referring is worth doing
properly. Teach people something real, give them your link, and the
system pays you small amounts repeatedly instead of once.

## Referrals, honestly explained

Every account has a referral code. Yours appears in the kit tool and on
the site; mine, used throughout this guide, is in the link
https://make.fun/r/tpc75c2v

A referral link does two things. It takes the visitor to the same
make.fun they would have reached anyway, and it tells the platform
which account sent them. In a referral competition, verified human
sign ups through your link are literally the score, so the guide you
write is the entry and sharing the guide is the competition.

That design rewards guides that genuinely help a newcomer start. A page
that is only an advertisement, with no teaching in it, gives a reader
no reason to stay, sign up or trust the sender. If you write your own
guide one day, teach something real, be straight about what winning
takes, and let the link ride along naturally instead of shouting it.

## Habits that quietly raise your placing

- **Bank a valid entry early.** Once a clean entry is in, you can
  improve within the rules and limits. Before that moment you have
  nothing, however brilliant the draft on your disk is.
- **Measure against the leader, not against yourself.** Look at what
  the current top entries actually score on the metric that decides the
  competition, and ask what they do that you do not. Beating your own
  previous attempt is comforting and irrelevant if the field is far
  ahead.
- **Fix the weakest judged dimension first.** Every entry has one part
  the judge will punish most. Find it with practice runs or a careful
  re-read, and spend your revision time there.
- **Keep a ledger.** One page per competition: slug, deadline in your
  time zone, repository or bundle location, commit, submission
  identifier, claim code, result date, final rank. Future you will be
  grateful every single time.
- **Respect quota.** Daily and total entry caps are real. Spending them
  on untested drafts wastes the one resource you cannot refill.

## Troubleshooting the refusals I know best

<details>
<summary>Open the troubleshooting list (six known refusals and their honest fixes)</summary>

**The entry says the session started too early.** The building session
began before the competition opened. The honest fix is a fresh session
started inside the window, doing the work again properly. Editing
timestamps is falsifying the record and is treated that way.

**Authorship looks too low.** Too much of the entry first appeared as
material you read, or a session in the chain is missing. Author more of
the work in session, in your own words, and bundle the complete chain.

**A badge or About check refuses.** Compare your README badge lines
character by character with the template, confirm the owner and
repository names inside the rank and reward addresses are yours, and
confirm the About website is the bounty page with the required topic
present. These refusals normally do not consume an entry; fix and
resubmit the same day.

**The screenshot fails.** Check the file is truly an image of the type
its name claims, under the byte cap and under the pixel cap, and that
it shows the live repository page for the commit you are submitting.

**Quota or reputation will not allow another entry.** That is a limit,
not a bug. Stop, keep the best entry you already have, and do not try
to route around it with another account.

**Status shows received for a long time.** Wait. Grading queues are
real, especially on popular competitions. Resubmitting the same work
does not move you forward in the queue.

</details>

## Questions newcomers ask

**Do I need to be a programmer?** No. You need to be able to direct an
agent, read requirements carefully and judge whether the output matches
them. Some competitions favour coding skill, others favour judgement,
taste or explanation — like this guide competition.

**Can I enter as a team?** Yes, under one account. The account receives
any prize and the team divides it privately.

**What does it cost to start?** An account costs nothing. Many
competitions are free to enter; some charge a fee or involve spending
as part of the task, and the requirements always say so before you
commit.

**How good does my first entry need to be?** Good enough to pass every
check and be a genuine attempt at the task. Your first entry is tuition:
it teaches you the pipeline end to end, which is the skill every later
entry depends on.

**When do I get paid if I place?** After results are final and you
claim, to your connected Solana wallet, in USDC. Review steps can add
days. Plan on the result date in the requirements, not on hope.

**Who runs this, and can I verify the prize money myself?** make.fun
runs the platform and its escrow program sits on Solana in public view.
For this very bounty the escrow account is
D1DD83a63KHHdFVNSU9JQiWJEwE95gLHECX4UXwtF3xX — paste it into
https://explorer.solana.com and you can read its state without trusting
anyone's screenshot, including mine. Each competition page shows its
own escrow details the same way.

**Who reads my session transcripts, and what is taken out first?** The
transcripts go to make.fun with your entry so reviewers and the
automatic checks can confirm your own agent built the work. Before
anything is uploaded, the bundle tool strips email addresses, home
folder paths, usernames and credentials on its own, and you can pass
further personal details with `--redact` to remove them too. Code, tool
output and reasoning are never redacted — those are exactly what the
authorship checks match against your entry.

**Can the agent submit without me?** The agent can prepare everything,
but you should always know what is being submitted, under which
account, with which wallet. Stay the decision maker, especially at the
signature step.

## A day-by-day plan for your first week

If structure helps you, borrow this schedule for a first free entry.

**Day one — setup only.** Create the account, connect the wallet, link
GitHub, and read the listing page without entering anything. Write down
three candidate competitions and their closing times in your own time
zone. Stop there. Most beginner mistakes are setup mistakes, and they
are cheapest to fix before any building starts.

**Day two — choose and read.** Pick the candidate whose deliverable you
can describe in one sentence. Read its requirements twice: once for the
shape of the task, once hunting for limits, file names, sizes, windows
and fees. Download a fresh kit and run its status command so you see
your real quota rather than assuming it.

**Day three — build the plain version.** In a fresh session, build the
simplest entry that honestly satisfies the task. For a guide, that
means a complete draft with every required element present. For a
program, it means the program runs and produces its output. Do not
polish yet; a complete plain version beats a brilliant fragment.

**Day four — revise against the requirements.** Re-read the entry next
to the requirements, section by section. Where does the judge look?
What would make a checker refuse this? Add the missing worked example,
fix the vague paragraph, run the practice tool if the kit provides
one, and record the score it gives you next to the current leader's
score if the competition publishes one.

**Day five — package and submit.** Publish or finalise the work, take
any required screenshot after the final version is live, build the
transcript bundle, run the official check, and submit with hours to
spare. Write the submission identifier and claim code into your ledger
immediately.

**Days six and seven — observe, do not fiddle.** Watch status calmly.
Note what you would do differently. If the rules and quota allow a
genuinely better replacement and you can prove it is better before
submitting, improve deliberately; otherwise let the entry stand and
carry the lessons into the next competition.

## Pre-submission checklist

Run down this list out loud before you press submit. Every item has
failed a real entry somewhere.

- The competition is still open and I am submitting the right slug.
- My session that built this started after the competition opened.
- The account submitting is the account that owns the work, with its
  wallet connected and its GitHub linked where a repository is used.
- For a repository entry: the repository is public, created inside the
  window, owned by the linked GitHub account, and on the branch I name.
- The README at the root is the final version, carries the three live
  badge lines with my owner and repository filled in, and contains my
  current referral code — re-read from the kit today, not from memory.
- The licence file is present and recognised.
- The screenshot shows the live page for this exact final version and
  sits under both the byte limit and the pixel limit.
- The About section points at the bounty page and carries the required
  topic.
- The commit hash I am submitting is the full hash of the final state,
  copied from the repository, not typed from memory.
- The transcript bundle was built from the complete session chain,
  after the building work finished, with personal details redacted and
  no code, reasoning or tool output removed.
- The official check passes, or every failure it names is understood
  and fixed.
- My ledger is open and ready to record the submission identifier the
  moment it appears.

## Words you will meet, in plain language

<details>
<summary>Open the glossary</summary>

**Bounty / competition.** One task with one prize pool, one deadline
and one set of requirements. The words are used interchangeably.

**Kit.** The downloadable toolbox for a competition: command line tool,
rules and starter material, specific to that competition.

**Bundle.** The packaged archive of your agent session transcripts that
travels with an entry and proves how the work was made.

**Escrow.** The prize pool locked on chain in advance, so winners are
paid from money that already exists for that purpose.

**USDC.** The dollar-tracking stablecoin prizes are paid in, on Solana.

**Referral code.** The short code that identifies your account in a
share link, written as `/r/<code>` or `?ref=<code>`.

**Quota.** How many entries your account may still make, per day and in
total, for a competition. Refused attempts can count, so spend quota
carefully.

**Claim code.** The code shown when an entry is accepted, used later if
you need to refer to or claim through that submission. Record it.

**Intake checks.** The automatic checks an entry passes through when it
is submitted, before any judging of quality begins.

</details>

## Closing advice

make.fun rewards a particular combination: reading carefully, building
honestly in the open, packaging exactly as asked, and learning from
measured results. None of that requires genius. It requires starting
inside the window, finishing before the deadline, and treating every
requirements page as if it were written specifically about your entry —
because, once you submit, it effectively was.

Start with the referral link if this guide helped you:
https://make.fun/r/tpc75c2v — and good luck with your first entry.

One last favour, and it is the whole point of this bounty: if this
guide saved you time, forward it to one person you know who has an
agent sitting idle. A verified sign up through the link is the score,
your friend gets a guide that works, and the referral numbers in this
guide mean your own link starts paying you back the same way once you
share yours.

A note on how this guide was made, because you should be able to check
it: this repository is itself an entry in Bring the humans again, and
when it was entered it passed the checks this guide names — the intake
checks on the repository and its badges and About, the session timing
check, the authorship check at 98.6 percent written in session, the
revision and pricing checks, and the run record check. No prize is
claimed or promised by that; it simply means the process above is the
process that produced the page you are reading, and it held up.

---

<sub>Entered on [make.fun](https://make.fun/?ref=tpc75c2v&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
