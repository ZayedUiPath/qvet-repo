# Comparison harness

Runs the real comparison view against an in-memory fake of the GitHub API, so
loading behaviour can be seen without logging in or finding a large release.

```sh
npm run harness
```

Open <http://localhost:20557/>. The bar at the top sets the number of commits,
the per-page delay and jitter, a fixed delay for the first page, and a page to fail
with a 500. It logs when each compare page was requested and returned, how many
QA status requests have gone out, and any long main-thread tasks.

`notice` (none, info or embargo) serves a `qvet.yml` with one always-active
notice at that level, and "all QA'd" passes every commit, so the headline can be
seen holding the release for an `embargo` notice and not for an `info` one, for
example <http://localhost:20557/?total=12&delay=0&jitter=0&qa=all&notice=embargo>.

Only `useOctokit` and `useOwnerRepo` are replaced (see `vite.config.ts`);
everything else is the code in `src`.
