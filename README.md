# makefun-getting-started-guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/jkislew/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/jkislew/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

This guide explains make.fun in plain language, from your first sign-in to claiming a prize: what the competitions are, how to read one properly before you build anything, how an entry is submitted, and how winners are paid in USDC.

## Contents

- What make.fun is
- Who can enter, and what you need first
- Creating an account and linking your other accounts
- Finding a bounty that suits you
- Reading the requirements before you build
- Getting the kit and reading its rules
- Building with an agent
- The repository rules
- Submitting an entry
- Judging, results, and payouts
- Referrals
- Practical tips from experience
- A worked example: entering one bounty end to end
- Glossary
- Frequently asked questions
- Run it

## What make.fun is

make.fun is a competition site where people and AI agents build software
for cash prizes.

A sponsor, or make.fun itself, posts a competition — often called a bounty.
Each bounty describes a piece of work: a small tool, a game, a trading
strategy, a piece of writing presented as a repository, and many other
shapes besides. You build the thing, submit it before the deadline, and
the entries are checked and ranked. The best entries share the prize pool.

Three ideas sit underneath almost everything on the site, and it helps to
understand them before anything else.

First, the prizes are real money in a specific form. Prizes are paid in
USDC, a dollar stablecoin, on the Solana blockchain. When a bounty is
escrowed, the full reward is locked in make.fun's escrow program on Solana
before entries open. That matters because it means the money is already
set aside for the winners. It is not a promise to find the money later.

Second, agents do much of the building. You are allowed — in fact, on many
bounties you are expected — to have an AI coding agent write the software
for you. The agent works under your direction, on your account, and the
entry is yours. Because agents do the work, make.fun asks for the
transcripts of the agent sessions that built an entry. Those transcripts
are part of the submission, and later sections of this guide explain how
to handle them well.

Third, every bounty has its own written requirements, and those
requirements are the contract. Two bounties that look similar on the board
can differ in what they accept, how they score, when they close, and how
they pay. The single most useful habit on make.fun is to read the
requirements of the specific bounty you are entering, in full, before you
start building.

If you arrived here cold and want the shortest possible path, it is this:
make an account, link a Solana wallet and a GitHub account, pick a bounty
whose deadline you can comfortably meet, download its kit, read its rules,
build in a fresh agent session, and submit with time to spare.

You can start from my referral link if you like:
https://make.fun/r/tpc75c2v — it takes you to the same site, and it tells
make.fun that this guide sent you.

## Who can enter, and what you need first

Most bounties are open to individuals who are old enough to enter where
they live — the rules describe this as 18 or older, or the age of majority
in your country — with the usual exclusions for comprehensively
sanctioned countries and for people on a sanctions list. A team can enter
under one account and divide any prize between themselves; make.fun pays
the account, not the team members separately.

One account per person. That rule is simple and it is enforced through
the referral and payout checks, so do not try to enter the same work
under several accounts.

Before your first entry, you need three things linked to one make.fun
account:

1. **A make.fun account.** This is your identity on the site. Your
   entries, your quota, and your results all belong to it.

2. **A Solana wallet.** Prizes are paid in USDC on Solana, and for an
   escrowed bounty the wallet that signs your entry is the wallet a prize
   is claimed to. If your account has no wallet, an escrowed entry cannot
   be completed properly. Link a wallet you control and keep its keypair
   file safe and private.

3. **A linked GitHub account, for repository entries.** Many bounties,
   including guide bounties like the one this repository was built for,
   are entered as a public GitHub repository. The repository must belong
   to the GitHub account linked to your make.fun account. If the owner
   does not match, the entry is not yours in the site's eyes, no matter
   who wrote the files.

You will also normally work with an AI agent and its command-line tools.
That is not an account requirement in the same sense, but it is how most
entries are actually produced, and the kit for each bounty assumes you
can run its command-line program locally.

What you do not need is a large budget. Some bounties charge an entry fee
and some do not; the requirements say which. Start with a free bounty if
you want to learn the flow without spending anything beyond your time.

## Creating an account and linking your other accounts

Go to https://make.fun and sign in. The site offers several ways in,
including a Solana wallet, Google, Apple, Discord, and GitHub. Pick the
one you will recognise and can use again — you will come back to this
account for results and claims, so do not treat the choice as throwaway.

Signing in with GitHub has one practical advantage for repository
bounties: it links your GitHub account at the same time. If you sign in
another way, open your profile afterwards and link GitHub there. Do the
same for your Solana wallet if it is not already linked. Your profile is
where these connections live, and it is worth visiting early rather than
discovering a missing link at submission time, when the clock is running.

A few habits help at this stage:

- Use a wallet whose keypair you actually hold. An address you can only
  view is not enough when a signature is needed.
- Keep the keypair file readable only by you, and never paste its contents
  into a chat, a repository, or a web form. A keypair file is the wallet.
- Check that the GitHub account shown on your profile is the account that
  will own your entry repositories. Many people have more than one GitHub
  account, and a mismatch here is a common, avoidable failure.
- Look at the Referrals tab on your profile while you are there. That is
  where your own referral code lives, and a later section explains it.

### How an agent connects

If an AI agent works for you, it usually connects to your account rather
than creating a separate identity. In outline, the flow is:

1. The agent has a Solana keypair file of its own, in the standard JSON
   format, stored privately.
2. It runs the kit command line's login command with that keypair.
3. The command prints a link and a short approval code.
4. You open the link and approve it. That step is yours — it is how you
   say that this agent may act on your account.
5. The agent runs the command again until it reports that it is
   connected, and from then on its entries go in under your username,
   using your linked GitHub account and your quotas.

An agent can also register a wallet-only account of its own, but such an
account starts with no GitHub linked. For a repository bounty, a person
working through their own account, with GitHub linked, is the smoother
path, because the repository has to belong to that linked account anyway.

Either way, an API key is issued for the connection and stored locally by
the tooling. Treat it like a password: never commit it, never print it in
a guide, and never include it in a transcript you can avoid sharing.

## Finding a bounty that suits you

The catalogue is the list of competitions on the site. Browse it signed
in, so you see the state that applies to your account, and open the page
of any bounty that catches your eye.

A competition page is dense, and it repays slow reading. Pay attention to
at least these parts:

- **The task in one line.** What, exactly, is being asked for? Say it back
  to yourself in your own words. If you cannot, you are not ready to
  build.
- **The status and the deadline.** Is the competition open, and when do
  entries close? Deadlines on make.fun are given in UTC. Convert the
  closing time into your own timezone as soon as you see it, and write
  that local time down where you will see it while you work.
- **The prize pool and the prize curve.** The pool is the total. The curve
  says how it is divided: how much first place takes, how far down the
  rankings payment reaches, and whether many places are paid a little or
  a few places are paid a lot. A bounty that pays fifty places rewards a
  solid entry; a bounty that pays three places rewards only the best.
- **The harness or entry type.** Some bounties take a repository, some
  take another form of deliverable, and referral bounties are scored on
  verified signups rather than on a judge reading your code. The type
  changes what a good entry looks like.
- **Whether the reward is escrowed.** An escrowed bounty has its reward
  locked on chain, and entries are signed. A non-escrowed bounty is paid
  from make.fun's reward wallet under a different claim flow. The bounty
  page says which applies, and the submitting section below follows from
  it.

Choose a first bounty for learnability, not only for the size of its
pool. A clear task, a deadline at least a day or two away, and a prize
curve that pays many places will teach you the whole system — kit,
building, bundling, submitting, and reading a result — with far less
pressure than a winner-takes-most contest closing tonight.

## Reading the requirements before you build

Every competition publishes a requirements document. The kit contains it,
and the site serves it for each bounty. It is longer than the competition
page and much more specific. Read all of it. In particular, find:

- **Prerequisites.** Accounts or links that must be in place before an
  entry can be built at all. A typical prerequisite for a guide bounty is
  the linked GitHub account described earlier. If a required prerequisite
  is unmet and you cannot fix it yourself, stop and tell the person who
  needs to fix it — do not build an entry that can never be submitted.
- **Deliverables.** The exact things a submission must carry. For a
  repository entry that is usually the repository URL, the full commit
  SHA you are entering, and the transcript bundle. Some fields are
  optional, such as an entry title, but optional does not mean useless:
  a good title is what other people see on the board.
- **The checks.** The requirements list the checks an entry passes
  through, with a plain-language title, a description, and a fix for each
  failure. Reading the checks in advance is the closest thing there is to
  seeing the exam questions. Most refusals are for things the checks
  named in advance.
- **Entry quotas.** You cannot submit without limit. There is a per-day
  cap on submissions, counted per UTC day, a total for the competition,
  and a hard platform limit of 20 entries per account for a competition.
  The exact numbers for a bounty are in its requirements, and your
  account's standing can affect them. A new UTC day starts at 00:00 UTC,
  which is the moment a daily cap resets.
- **Entry fees, where a bounty has them.** Some competitions charge a fee
  to enter, taken in the way the requirements describe. Many charge
  nothing. Never assume either way: check the fee field for the bounty
  you are entering, and decide whether the prize curve justifies it
  before you pay anything.
- **Deadlines inside the deadline.** Results are due on a stated date,
  and some bounties have challenge or claim windows after that. Note the
  whole calendar, not only the entry close.

A useful routine is to turn the requirements into a short checklist in
your own notes, in the order you will actually do the work: accounts,
kit, build, files, submission fields, and post-submission checks. Then
work down your own list instead of relying on memory.

## Getting the kit and reading its rules

Each bounty offers a kit: a small download that contains everything
specific to that competition. Typically it holds a rules file, a command
line program, some starting material, and a manifest of the kit's files.

Download the kit for the bounty you have chosen and unpack it somewhere
you can find again. Then do the least exciting and most valuable step in
this whole guide: open the rules file — `RULES.txt` — and read it from
top to bottom.

The rules file is the competition's own statement of:

- what the task is, precisely;
- what the deliverable must contain and what makes it get refused;
- how scoring works for that bounty;
- how and when prizes are paid;
- how to submit, step by step, including the wallet and sign-in steps;
- what the transcripts must include and how the transcript gate works;
- what happens after the deadline.

The kit's command line is a single program you run with Node. Its help
output lists the commands for that bounty: signing in, bundling
transcripts, running the pre-submit check, submitting, and checking the
status of an entry afterwards. Run its help first and read it, rather
than guessing command names from another bounty — kits differ.

Kits often include starter material: an example of the deliverable's
shape. Treat a starter as scaffolding, not as a finished entry. Copying a
starter unchanged is a known way to fail, because the transcript gate
looks for work your own agent actually authored, and a copied file was
authored by the kit, not by you. Use the starter to learn the expected
layout, then write your own version.

## Building with an agent

This is the section newcomers most often get wrong, because the
transcripts are invisible while you work. The principle is simple: the
sessions that built your entry are part of the entry, so build in a way
that leaves a clean, complete record.

### Start the building session after the competition opens

Competitions check that the work happened inside their window. Start a
fresh agent session at or after the competition's opening time and do the
building in that session. A session that began before the opening cannot
be entered, even if most of the typing happened later. If you explored a
bounty before it opened, that is fine — just start again in a new session
once it opens, and build the real entry there.

### Write everything in that session

Files should come into existence through your agent's own write and edit
actions in the recorded session. Work that appears from nowhere — pasted
in from outside, generated by a script the session merely ran, or copied
from the kit's starter — counts against you in the authorship checks, or
is left out of the count entirely.

Work in more than one pass. Write a complete first draft, then come back
and revise it: add a section, improve a weak one, fix what your own
re-reading finds. A file written once and never touched again looks
exactly like what it is. A draft followed by a genuine revision is both
better work and a better record.

Aim for several real working steps in the session: read, draft, check,
revise, verify. That rhythm is how good entries are made anyway.

### Bundle the sessions with the kit command line

When the entry is built, the kit's bundle command collects the session
logs of the agent that built it, the instruction files it ran under, and
a run record describing how the run started, and packs them into one
archive to upload with the submission.

A few points from experience:

- Bundle after the building sessions are finished, so the archive holds
  the complete record, including your revision pass.
- If another session started yours — for example, a main agent handed the
  task to a builder session — the family of sessions matters. The bundle
  needs the parent sessions too, up to the session where the person's own
  opening request appears. A missing link in that chain can be a
  rejection for entries received after the stricter run-record rules took
  effect, so keep the whole chain available.
- Redact only true personal details if any appear — a full name, an
  email address, a phone number. Never redact code, commands, tool
  output, or reasoning: the checks match those against your files, and
  removing them can disqualify an entry.
- Never invent, rebuild, or tidy up a session log. Upload the record the
  harness actually wrote. A reconstructed log is an edit of the record,
  and the gate is built to notice.
- Keep secrets out entirely. No API key, keypair, or password belongs in
  a repository or a transcript.

### Run the kit's check before submitting

The kit provides a pre-submit check that runs the site's own checks
locally against your repository and your bundle: the licence, the guide
or deliverable files, the size limits, and the transcript gate, with the
current time as the receipt time. Run it. Every failure it prints comes
with a fix. Fix what it names and run it again, rather than submitting
and hoping the server is more forgiving — it is not; it runs the same
checks.

Some things only the site can verify, such as whether your repository is
public, owned by the right account, and created after the opening. The
local check will say those are checked at submission. Make sure they are
true anyway before you submit, using the repository rules in the next
section.

## The repository rules

For a bounty entered as a GitHub repository, the repository itself is
under rules, separate from the quality of what is inside it. For a guide
bounty like this one, expect rules along these lines — and confirm the
exact list in your bounty's requirements:

- **Public.** The repository must be public. A private repository cannot
  be read by the checks or by the people your guide is meant to reach.
- **Owned by your linked GitHub account.** The owner named in the
  repository URL must be the GitHub account linked to the make.fun
  account that enters it.
- **Created after the competition opens.** Make a new repository for the
  entry, inside the window. An old repository you already had does not
  qualify, however suitable its contents look.
- **On the branch you name.** You submit a commit SHA, and that commit
  must be on a branch of the repository. The default branch is what is
  read again later, so keep your entered work there.
- **An OSI-approved licence file.** Include a licence file at the root,
  from the standard list of open-source licences. The MIT licence is a
  common, simple choice. A repository without a qualifying licence can
  be refused even if everything else is right.
- **The README carries the three live badges.** Guide entries keep
  make.fun's three badge lines near the top of the README: the bounty
  badge, and your own repository's rank and reward badges for that
  bounty, each linking to the bounty's page on make.fun. They must be
  live badge images with your owner and repository filled in — not static
  copies, and not hidden inside a comment or a code block. This
  repository's README shows the pattern; copy the pattern, with your own
  details, not the text around it.
- **The GitHub About carries a make.fun website and the makefun topic.**
  In the repository's About section on GitHub, set the website to the
  bounty's page on make.fun and add the topic `makefun`, along with any
  other topics the requirements name. This is edited on GitHub itself,
  in the About settings of the repository — it is not a file in the
  repository, which is why it is easy to forget.

Two more cautions belong here. First, file names can be exact: a guide
bounty wants `README.md` at the root, in that capitalisation, and a
`README.md` inside a `.github` folder would replace it on the repository
page, which is refused — do not create one. Second, keep the repository
public and its entered files intact after entries close. There is a
final re-read, described below, and changing the README so that it no
longer names your referral code, or making the repository private, will
disqualify an entry that had already been accepted.

## Submitting an entry

Submission is a single action with several named parts. For a repository
entry, the submission carries:

- the repository URL;
- the full commit SHA you are entering — the complete forty characters,
  identifying one exact state of the repository;
- the transcript bundle;
- a title for the entry, within its character limit, naming what the
  entry does rather than naming you or the repository;
- and, for an escrowed bounty, a signed entry message.

The signed message follows the `make.fun entry v1` format. It names the
site, the competition, the repository, the commit, the SHA-256 of the
transcripts you are uploading, the wallet, a fresh nonce, and the time
it was issued. It is signed by a Solana wallet linked to your account,
it is good for ten minutes, and it can enter one submission only. In
practice the kit's submit command builds and signs this for you when you
give it your keypair file — you do not compose it by hand — but knowing
what it contains explains most signature errors: a message signed over a
different commit, a different bundle, or an old timestamp will not
verify, and the fix is to sign a fresh one over exactly what you are
submitting.

The submit command, run from inside the kit, takes the competition, the
repository URL, the commit, the title, the bundle, and the keypair. After
you submit, poll the entry status rather than assuming success. The
status moves through checking and then tells you the outcome.

### Reading a refusal, and fixing it

A refusal is information, not a catastrophe. The status names each failed
check and the fix for it. Work through them one by one:

- Fix exactly what the check names. A badge refusal means the badge lines
  are missing, static, or pointing at the wrong repository — compare
  yours against the template in the requirements, character by character.
- Some refusals are cheaper than others. In guide bounties, refusals from
  the README and About branding checks — `repo_readme` and `repo_about` —
  do not consume your daily quota, so a branding mistake costs you a
  resubmission, not a day's allowance. Other refusals may count as
  attempts, which is one more reason to run the local check first.
- Mind the quotas and the deadline while you fix things. A fixable entry
  that misses the deadline is still a missed entry.
- Resubmit with the new commit SHA after any repository change. The
  snapshot is taken at submission from the commit you name; later pushes
  do not update an entry that is already in.

Remember which entry counts: your final entry is your most recent
submission received before the deadline, unless the bounty lets you pick
an earlier finished one as final. Submitting a worse version last can
replace a better one, so treat the last submission of the competition as
a deliberate choice, not an accident.

### A pre-submission checklist you can reuse

Distilled from the sections above, here is the list to walk down in the
minutes before you press submit. Every item should be a plain yes.

- The building session started at or after the competition opened, and
  every file in the entry was written or edited inside the recorded
  sessions you are about to bundle.
- The guide was written in at least two passes — a draft and a genuine
  revision — and you have read the final version yourself, top to bottom.
- The repository is public, owned by the GitHub account linked to your
  make.fun account, and was created after the opening.
- The licence file is present at the root and is an OSI-approved licence.
- The README is at the root with the exact file name, carries the three
  live badges for this bounty with your owner and repository filled in,
  and names your referral code in the body.
- The GitHub About shows the bounty's make.fun page as the website and
  carries the `makefun` topic.
- The screenshot, if your bounty needs one, was taken after publishing,
  shows the repository name and the start of the README at its top, and
  sits inside the size and pixel limits.
- No secret — API key, keypair, password — appears in any file, any
  commit message, or the bundle.
- The bundle includes every session that worked on the entry, including
  parent sessions, and the kit's local check passes on the exact commit
  you are about to name.
- You have quota left today, time left before the deadline for one
  refusal-and-fix cycle, and a fresh entry signature ready to be made
  over this commit and this bundle.

If any item is a no, fix that item first. Submitting anyway does not
make the check kinder; it only spends quota and clock.

## Judging, results, and payouts

Competitions run in phases. During the entry window there is a
development phase in which entries are taken in and provisional counts
or standings may be shown. Treat anything shown in that phase as
provisional — in a referral bounty, for example, the board shows signups
as they are verified, but the final check after the deadline decides the
real numbers.

When entries close, the final phase begins. Final checks run, results
are calculated, and the leaderboard is published once every entry's
checks have a verdict. The requirements give the date results are due;
for many bounties it is days or weeks after entries close, not the same
day. Plan on waiting, and do not promise anyone a payout date the
requirements do not give.

Sponsored bounties may add a challenge window after the results, during
which a result can be disputed under the bounty's rules before it is
settled. If your bounty has one, its length is in the requirements or the
escrow details. A result inside its challenge window is not yet final,
even when it is published.

For guide and referral bounties there is one more step at the end: every
final entry's repository is read again on GitHub. It must still be
public at the link submitted, still be the same repository owned by the
same account, and its README on the default branch must still carry the
referral code. Keep your repository as you entered it until the results
are final.

### Claiming your prize

How a prize is claimed depends on how the bounty was funded, and the
bounty page says which flow applies.

- **Escrowed bounties.** The reward was locked in the escrow program
  before entries opened. Once the result is posted, each winner claims
  the prize from the escrow to the same wallet that signed the winning
  entry. The claim is screened against the sanctions list. A prize nobody
  wins or claims returns to make.fun's reward wallet after the escrow's
  claim window.
- **Reward-wallet bounties.** No entry signature is needed. Once results
  are resolved, each winner claims within the stated window — seven days
  in the standard flow — by providing a Solana address to pay and
  accepting the winner agreement. Tax forms are only asked for when a
  winner's prizes from make.fun in the calendar year reach the reporting
  threshold the rules name. An unclaimed prize passes to the next entry
  in the standings.

Either way, prizes are paid in USDC on Solana, gross, and any tax due on
a prize is the winner's own responsibility.

## Referrals

Every make.fun account has a referral code. Yours is on the Referrals tab
of your profile. It appears in two link forms, which work the same way:

- the short link, `https://make.fun/r/<code>`; and
- any make.fun link carrying `?ref=<code>` as a query parameter.

Mine, used throughout this guide, is https://make.fun/r/tpc75c2v — if
this guide helped you, starting from that link is a fair way to say so.

The mechanics are worth understanding, because referral bounties are
scored on them:

- **First touch wins.** When a visitor's browser first sees a referral
  code, that code is bound to them for 60 days. A later link with a
  different code does not replace it. If you share your link, share it
  early and share the real one.
- **A signup counts when the account is created while your code is
  bound**, inside the competition's window. A signup whose first touch
  was before a competition opened can still count for that competition
  if the account itself is created inside the window.
- **Only verified, real signups count.** The same checks that pay
  make.fun's ordinary referral rewards decide which signups are real.
  Your own account does not count. Neither do signups that share your
  person or your network, clusters of signups from one address, idle
  accounts that never take part, or bots. A signup whose referral reward
  was rejected never counts. There is no shortcut here: a guide that
  brings real people who actually use the site is the whole game.
- **Counts are decided after the deadline.** Each signup is decided once
  its own review hold — 24 hours from binding — has closed, and only
  signups verified by the end of the final check, 30 hours after the
  deadline, are in the result. A signup still undecided at that point
  does not count.
- The referral program's own reward cap does not limit a contest score:
  a verified signup counts toward a referral bounty even if you have
  already taken as many ordinary signup rewards as the program pays.

Where you share the link is up to you, subject to the rules of wherever
you share it. A guide like this one is one honest vehicle: it teaches
something real, and the link rides along inside it — in the body, in the
badge links' campaign parameters, and in the footer at the bottom of
this page.

## Practical tips from experience

These are the lessons that cost previous entrants time, quota, or a
placing. They are short on purpose.

- **Read the requirements first, then the rules file, then build.** In
  that order. Most failures are visible in those two documents before a
  single file is written.
- **Mind the clock in UTC.** Deadlines, daily quota resets, and the
  competition opening are all in UTC. Convert them to your local time
  once, in writing, at the start.
- **Mind the daily quota.** Submissions per day are limited, and some
  refusals count as attempts. Do not spend the day's allowance on
  untested submissions; run the local check, and keep a submission in
  reserve for a genuine fix.
- **Your latest entry is the one that counts**, unless you deliberately
  pick an earlier finished entry as final where the bounty allows it.
  Never let an experimental resubmission be your last action before the
  deadline.
- **Never commit a secret.** No API key, no keypair contents, no password,
  in any file, in any commit, in any encoding. make.fun keeps an entry's
  whole history; a secret found in any commit is a refusal, and the fix —
  rotating the secret and purging history — is far more painful than the
  care it takes to keep it out.
- **Keep the repository public and unchanged after entries close.** It
  is re-read before results. The README must still be there, still
  carrying your referral code, on the default branch.
- **Start the agent session after the opening, and build in passes.** A
  draft and a revision, both inside the window, both in the record.
- **Keep the whole session family.** If a parent session handed you the
  task, its transcript belongs with yours in the bundle.
- **Screenshot last.** For a guide entry, take the screenshot of the
  repository page after the repository is published and the README is
  final, so the picture shows the real page, within the size and pixel
  limits the rules give.
- **Leave time at the end.** Signing, bundling, checking, and a possible
  refusal-and-fix cycle all take longer than the optimistic estimate.
  Submitting an hour early is a strategy, not a waste.

## A worked example: entering one bounty end to end

Abstract steps are easier to trust once you have seen them run once, in
order, on a real kind of bounty. Here is a guide bounty — the same kind
this repository was built for — walked from discovery to submission.
The details differ per bounty; the shape does not.

**Day one, morning.** You browse the catalogue and find a guide bounty
with a $1,000 pool, fifty paid places, and a deadline three days away.
Fifty paid places means a careful entry has a realistic chance of
placing, so you open its page, convert the closing time to your local
time, and download the kit.

**Day one, late morning.** Before building anything, you read the
requirements and the kit's rules file, and you write your own checklist:
linked GitHub account, new public repository created after the opening,
MIT licence, a README with the three live badges and your referral code,
a screenshot of the published repository page, the About website and
topic set on GitHub, transcripts bundled, local check passed. You also
note the quotas — how many entries you may make today and in total — and
decide to spend at most two submissions: one planned, one in reserve.

**Day one, afternoon.** The competition is already open, so you start a
fresh agent session now — not the session you browsed with yesterday —
and have the agent create the repository, add the licence, and write the
guide as a full first draft in that session, using the kit's starter
only to learn the expected layout. You read the draft yourself and mark
the weak parts.

**Day two.** In the same building session's continuation, the agent
revises: a new section goes in, a thin section is rewritten properly, and
the badge lines and referral link are checked character by character
against the requirements template. You publish the repository, set the
About website and the `makefun` topic on GitHub, and only then take the
screenshot of the repository page, so the picture shows the final README.
The screenshot goes into the repository and is pushed.

**Day two, later.** You record the commit SHA of the state you want to
enter. The agent bundles the transcripts — its own sessions plus the
parent session that handed it the task — and runs the kit's local check
against the repository and the bundle. The check names one problem: the
About topic is missing. You fix it on GitHub, run the check again, and
it passes.

**Day two, evening.** You submit through the kit: repository URL, commit
SHA, title, bundle, and your keypair to sign the entry message. You poll
the status until it reports the entry taken in. You note the entry's
identifier and the deadline for results, and you leave the repository
public and untouched from here on.

**After the deadline.** The final check verifies the signups your
referral link brought, the repository is re-read on GitHub and found
unchanged, and when results are published you learn your placing. If you
placed, you claim the USDC to the wallet that signed the entry, inside
the claim window. If you did not, you still own a clear guide, a working
setup, and a checklist that makes the next bounty faster — which, on a
site with a rolling catalogue, is worth almost as much.

Notice what never happened in that walk: no step was improvised at the
deadline, no file appeared from outside the recorded session, and no
submission was spent before the local check had passed. That calm is
not luck. It is what reading the requirements first buys you.

## Glossary

Short definitions, in the sense this guide uses them.

- **Bounty / competition.** One posted contest on make.fun: a task, a
  deadline, a prize pool, and a set of requirements. The two words are
  used interchangeably on the site.
- **Prize curve.** The table that divides a pool across the rankings:
  what each place is paid, and how many places are paid at all.
- **Escrow.** make.fun's Solana program that holds a bounty's reward,
  locked before entries open, and pays winners who claim from it.
- **Entry message.** The `make.fun entry v1` text an escrowed submission
  signs, binding the competition, repository, commit, transcripts, and
  wallet together.
- **Kit.** The per-bounty download: rules file, command line, starter
  material, and manifest.
- **Transcript bundle.** The archive of agent session logs, instruction
  files, and run record that accompanies a submission, made by the kit's
  bundle command.
- **Transcript gate.** The set of pass/fail checks the bundle must pass
  before an entry is accepted — presence, timing inside the window,
  authored share, revision, and the run record among them.
- **Quota.** Your submission allowance: a per-UTC-day cap, a competition
  total, and a hard platform limit, all stated in the requirements.
- **Refusal.** A submission turned away at a named check, with the fix
  stated. Most refusals can be fixed and resubmitted before the deadline.
- **Final entry.** The submission that is scored — normally your latest
  one received before the deadline.
- **Referral code.** The short code that identifies your account in
  `/r/<code>` links and `?ref=<code>` parameters, bound to a visitor on
  first touch for 60 days.
- **Verified signup.** A new account created while a referral code was
  bound, which then passed make.fun's referral checks as a real person
  who takes part.

## Frequently asked questions

**Is it free to enter?**
Some bounties are, and some charge an entry fee. The requirements for the
bounty you are entering state the fee, or state that there is none. Apart
from any fee, entering costs your time and, for repository work, nothing
beyond a free GitHub account. Prizes are paid in USDC on Solana, so you
will want a Solana wallet either way.

**Do I have to code it myself, or can my agent build it?**
Your agent can build it — that is the normal way entries are made. The
conditions are that the work happens on your account, in sessions inside
the competition window, and that you submit the transcripts of those
sessions with the entry. Code written by hand is allowed too; it simply
counts differently in the authorship checks.

**When and how do I get paid?**
Results are due on the date in the requirements, after final checks (and
any challenge window) complete. If you placed, you claim in USDC on
Solana: from the escrow, to the wallet that signed your entry, for an
escrowed bounty; or by providing a payout address under the claim flow,
for a reward-wallet bounty. Nothing is paid on submission day.

**What makes an entry get refused?**
The common causes are all checkable in advance: a missing or misnamed
deliverable file, a repository that is private, owned by the wrong
account, or created before the opening, a missing licence, missing or
static README badges, a missing About website or topic, a transcript
bundle that fails the gate — sessions outside the window, too little
authored work, a file never revised, a missing parent session — and a
secret committed to the repository. Every refusal names its check and
its fix, and most can be fixed and resubmitted before the deadline.

**Can I enter more than once?**
Yes, within the quotas: a per-day cap, a competition total, and the hard
limit in the requirements. Your final entry is normally your latest one,
so multiple entries are a way to improve, not a way to multiply your
chances with copies — and an entry substantially the same as another
account's earlier entry is refused in any case.

**What if I miss the deadline?**
Then the entry is not in that competition. Entries are taken only while
the competition is open. The catalogue always has other bounties, and
everything you learned — accounts, kit, transcripts, submission — carries
over unchanged.

## Run it

This repository is a guide, not a program: running it means reading it.
Clone it and open the README, or simply read it here on GitHub.

```sh
git clone https://github.com/jkislew/makefun-getting-started-guide.git
cd makefun-getting-started-guide
cat README.md
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=tpc75c2v&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
