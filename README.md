# renovate-beachball-demo

Demo of a repo which requires [beachball](https://microsoft.github.io/beachball/) change files for updates to monorepo packages.

As a demo, there's just one package under `packages/pkg1`, it's not private, and its only dependency is React.

`.github/workflows/check-change.yml` verifies the presence of beachball change files for every change that touches a non-private package.

Change files are created under `/change`. To show what this looks like, I manually created a change file for one [Renovate PR](https://github.com/ecraig12345/renovate-beachball-demo/pull/5) and merged it. (In a real repo there would be a publish workflow that picks up the change files and bumps the packages accordingly, either on some schedule or on demand.)

There's [another open Renovate PR](https://github.com/ecraig12345/renovate-beachball-demo/pull/3) which fails the check due to missing change files.

`renovate.json` has my guess at what the proper config would be if beachball was enabled. Right now it uses a generic message, but it would be ideal if the same message that renovate will use for the commit could be used for the change file (maybe through some kind of variable substitution if you have that?).
