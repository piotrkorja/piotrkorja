Your Gemfile is clean and modern (Rails ~> 8.1.2, solid_* stack, Google OAuth via omniauth-google-oauth2, Drive/Sheets APIs, etc.) — no obvious conflicts or dead weight for a logistics/prototype app.

Since you're asking about **Audited** vs **New Relic** (or alternatives) in this context:

- **Audited** — perfect fit for your needs right now  
  You need audit trails for model changes (serial numbers, statuses, write-offs, incident submissions, who changed what/when).  
  Audited is lightweight, actively maintained (compatible with Rails 8.0/8.1 as of late 2025 updates — they relaxed the gemspec for 8.1), and integrates seamlessly with ActiveRecord.

  **Why Audited over others?** (based on 2025–2026 ecosystem)
  - Simpler and faster than **PaperTrail** for basic "who did what" logging (fewer forks/breaking changes recently).
  - Better than **Logidze** if you don't want DB triggers/JSONB overhead or PostgreSQL-specific magic (your app is on pg, but Logidze adds complexity for marginal perf gain in a small/medium app).
  - Zero-cost, easy to query (`audits` table), supports `associated_with: :user`, custom audits, and works well with your existing `users` + `logs` table if you want to extend later.
  - No performance hit for your scale.

  **Quick add to your Gemfile**:
  ```ruby
  gem 'audited', '~> 5.6'   # or '~> 5.0' if you want conservative
  ```

  Then:
  ```bash
  bundle install
  rails generate audited:install   # creates audits table + migration
  rails db:migrate
  ```

  In models (e.g.):
  ```ruby
  class EquipmentItem < ApplicationRecord
    audited  # or audited associated_with: :unit / :user
  end

  class WriteoffCase < ApplicationRecord
    audited
  end
  ```

  Done — you get automatic create/update/destroy logs with user_id (if `current_user` is set via controller concern), IP, changes diff.

- **New Relic** — **not** recommended yet  
  It's enterprise APM (performance tracing, slow queries, memory, error rates, infra metrics).  
  Your app is a prototype on Fly.io — New Relic would be overkill (expensive per host/user, heavier agent, more setup).  
  Use it later if you hit real traffic/performance pain (e.g. slow Drive API calls or Solid Queue jobs).

- **Better alternatives for error/performance monitoring on Fly.io (2026)**  
  1. **Sentry** (top choice for you)  
     - Excellent error grouping + breadcrumbs + session replays.  
     - Has basic performance tracing (enough for Rails).  
     - Fly.io officially supports/credits it.  
     - Free generous tier → scales well.  
     - Gem: `gem 'sentry-rails', '~> 5.0'` (add `sentry-ruby` too).  
     - Setup: 10–15 min, great for catching 500s on `/volkodav` submissions, background jobs, OAuth fails.

  2. **Skylight** or **Scout APM** (if you want pure Rails-optimized APM)  
     - Skylight: dead-simple install, amazing N+1 detection, low overhead.  
     - Scout: strong on Rails/Python, good error + perf in one.  
     - Both cheaper than New Relic (~$20–50/mo), less noisy.

  3. **AppSignal** — if you want Ruby-first APM + errors + logs in one nice UI (popular in EU).

**My prioritized recommendation for your current stage**:
1. Add **Audited** now → solve your core need (tracking changes to sensitive data like UAV codes, statuses, incidents).
2. Add **Sentry** next → catch crashes/errors in production (especially important once OAuth is live and sergeants start submitting).
3. Defer full APM (Skylight/Scout/New Relic) until you see real slowness or have budget/scale.

If you want, I can give exact config snippets for Audited + user stamping, or Sentry integration tailored to your Google OAuth / Drive setup.  

Which direction — install Audited first, or jump to error monitoring?