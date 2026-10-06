# Memory Loop Test 1 — Tempo Lab

## Architecture and decisions
- Static single-page rhythm memory game on Vercel, source in GitHub `perryaiassistant-cloud/memory-loop-test-1`.
- Four Web Audio guide beats at the chosen BPM, followed by eight user taps. The first tap starts the sequence; seven intervals determine timing score, average gap, and drift.
- Browser localStorage keeps the five most recent rounds. No backend, login, or personal data. This exercises timing, audio, state transitions, persistence, and accessible keyboard input rather than CRUD.
- Production URL: https://memory-loop-test-1.vercel.app/
- Vercel project ID: `prj_B1FBGPqP7atzjAJS7UGvEBhCo4ff`; verified deployment: `dpl_EoDQNeuzFyRbs5G9Lscwn1DgTxs4`.

## Failures and fixes
1. Inline Vercel deployment initially rejected missing project settings. Created the Vercel project first.
2. Vite build then failed with exit 127 because no package manifest existed. Added `package.json` with Vite dependency and redeployed successfully.
3. Browser runner lacked native Chromium libraries; installed Playwright browser dependencies. Local proxy certificate required `ignoreHTTPSErrors` in the verification runner.

## Verification (2026-10-06 UTC)
- Vercel reported deployment READY. Production domain returned HTTP 200.
- Playwright browser completed a full eight-tap round at 100 BPM: score 97%, average interval 616 ms.
- The round remained in history after reload. Clear best removed it. No page errors.
- Verification script: `verify.cjs` in the local output artifact. It depends on a local Playwright installation.

## Old test cleanup
- Folio Tasks Vercel project: `folio-tasks-20261003`, ID `prj_YfIKPvrVwv2oWBJ55D8WIYzsFvpJ`, three READY deployments, default Vercel domain.
- Folio Tasks Supabase project: `folio-tasks-20261003`, ID `fxiklfpzejogcalvupfm`, healthy, one `public.tasks` row, one migration.
- Whole-project deletion requires user approval. Connected Vercel and Supabase tools do not expose whole-project deletion. Neither resource was deleted.
- The connected tools also lack an operation to create or move a project into the requested `Test Projects` group; the GitHub and Vercel resources exist under the requested name, but group placement remains outstanding.
