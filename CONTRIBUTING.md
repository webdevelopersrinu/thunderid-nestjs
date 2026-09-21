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
- **Publish** (`.github/workflows/publish.yml`) runs only when a
  maintainer publishes a GitHub Release. It builds, tests, then runs
  `npm publish`. Nobody runs `npm publish` by hand.
- Contributor avatars in the README update via the all-contributors
  bot — comment `@all-contributors please add @<username> for code`
  on your merged PR.

## What's manual (maintainer does this to cut a release)

1. Make sure every merged PR since the last release added a
   changeset (`npx changeset`).
2. On `main`, run `npx changeset version`. This bumps the version in
   `package.json` and writes `CHANGELOG.md` from the changesets.
3. Commit that (`git commit -am "release vX.Y.Z"`) and push to `main`.
4. On GitHub: **Releases → Draft a new release**, tag it `vX.Y.Z`,
   title it `vX.Y.Z`, paste the new CHANGELOG.md section as the
   description, click **Publish release**.
5. Publishing the release triggers the `Publish` workflow, which
   builds, tests, and pushes the version to npm.
