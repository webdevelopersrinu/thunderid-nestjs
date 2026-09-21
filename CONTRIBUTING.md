# Contributing

Thanks for looking at this. Small SDK, easy to contribute to.

## Before you write anything

Read `MY-CONTRIBUTION-RULES.md` in this repo (or ask the maintainer for
it). Short version: write short, write simple, write like you talk.
Skip the "This PR introduces a comprehensive..." tone.

## Setup

```
npm install
npm run build
npm test
```

## Making a change

1. Branch name: short, lowercase, dashes. `fix-guard-redirect`, not
   `feature/comprehensive-guard-fix-v2`.
2. Write the code. Comment only when the WHY isn't obvious.
3. Add a changeset:
   ```
   npx changeset
   ```
   It asks what changed and how big (patch/minor/major). Write one
   plain sentence, like you'd tell a teammate.
4. Open the PR. Description: 3-5 short sentences, what was broken,
   what you changed, that tests pass.

## What happens automatically (you don't need to do this)

- **CI** (`.github/workflows/ci.yml`) runs lint, typecheck, build, and
  tests on every push and PR.
- **Release** (`.github/workflows/publish.yml`) runs on every push to
  `main`. If there's a pending changeset, a bot opens (or updates) a
  "Version Packages" PR — that PR IS the changelog for the next
  release, open for anyone to read before it ships.
- Merging that PR publishes the new version to npm and writes
  `CHANGELOG.md`. Nobody runs `npm publish` by hand.
- Contributor avatars in the README update via the all-contributors
  bot — comment `@all-contributors please add @<username> for code`
  on your merged PR.

## What's manual

- Writing the code and the changeset.
- Reviewing PRs.
- Deciding what's a patch vs minor vs major (the changeset prompt
  asks you, use your judgment).
