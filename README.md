# Pre-Send Check

A prototype tool for matchmakers. It checks every profile against the client's preferences **before** it is sent, so clients stop receiving profiles they have already said no to.

Built for The Date Crew Product Growth Assessment.

**Live demo:** https://claude.ai/artifact/JMTgvymvNLMdPuBpNtTE9X

## The problem it solves

In the last 30 days, only 31% of shared profiles were accepted. About 35% of the rejections broke a preference the client had already given (smoking, children, diet, city). That is roughly 24 of every 100 profiles sent: guaranteed rejections that waste the client's patience and the matchmaker's time.

## What it does

For each client, the candidate pool is split into three lists:

- **Blocked**: breaks a deal-breaker, with the exact reason (for example, "Smoking: Yes (wants No)"). The matchmaker can override, but only with a written reason.
- **Needs a check**: a deal-breaker field is missing on the candidate's profile. **Ask candidate** drafts an email asking for it. Recording the answer moves the profile to Ready or Blocked.
- **Ready to send**: passes every deal-breaker, ranked by fit with softer preferences (city, age, education, drinking, interests), with reasons.

**Log a rejection:** paste the client's feedback. It is turned into tags (Location, Diet, Career and so on). For each tag, the matchmaker saves it as a **deal-breaker** (blocks profiles) or a **preference** (changes ranking only). The suggested option is based on the client's wording.

## How to run it

Open `index.html` in any browser. There is no build step and nothing to install.

## How the AI part works

- **Deal-breaker rules and ranking** are plain JavaScript. AI isn't needed for clear facts.
- **Reading rejection feedback** uses Claude when the page is opened on claude.ai (the live demo link). Anywhere else, including opening the file locally, it falls back to simple keyword rules and says so on screen.
- **In production**, a decision model such as Jev (TypeSafe AI) could handle the classification steps, with Claude for writing emails and explanations. This would be tested against past decisions before being trusted.

## Data

All clients and candidates are made up. No real personal data is used.

## Files

- `index.html`: the whole prototype (HTML, CSS and JavaScript in one file)
- `README.md`: this file
