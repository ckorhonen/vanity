# Vanity development guide

This is the legacy Ruby/Rails experiment framework. `lib/vanity/` owns adapters, experiments, metrics and Rails integration; `bin/vanity` is the CLI, `generators/` contains Rails generators, `test/` contains Test::Unit coverage, and `doc/` is the documentation source. Start with `README.rdoc`, `Rakefile`, and the affected source/test pair.

## Setup and verification

`.rvmrc` selects Ruby 1.9.2; `.travis.yml` and `Rakefile` also cover 1.8.7. `Gemfile` pins Rails 2.3 and old native dependencies. Use a compatible isolated Ruby/Bundler environment and `bundle install`; do not modernize dependencies merely to make a documentation task pass.

From the root, `bundle exec rake test` is the default test gate; `bundle exec rake test:all` runs Redis, MongoDB and MySQL adapters. `test/test_helper.rb` defaults to Redis database 15 and flushes test data; use disposable databases only. Native database clients and running test services are prerequisites. `test:rubies` installs RVM versions/gemsets, so it is not a harmless check. No separate lint/typecheck task is defined.

`bundle exec rake build` builds the gem. Documentation uses Jekyll/RedCloth, YARD, zip and wkhtmltopdf through `rake docs`. `rake install`, `push`, and `publish` install locally or publish remotely; they are not validation commands. Preserve Rails compatibility and add regression coverage for adapter or tracking changes.

## Completing work

Follow the nearest repository instructions and existing patterns; preserve unrelated edits. Make routine reversible choices within the request and continue through implementation, relevant checks, and repair of failures caused by the change. Ask only for material product decisions, missing prerequisites, or actions outside the authorization. Deployment, publishing, credentials, destructive operations, and live external effects need authorization for that scope.

Choose checks for the affected behavior and existing required gates; do not broaden into unrelated cleanup. For instruction-only edits, inspect source references and run `git diff --check -- AGENTS.md` (include any other changed instruction paths). Report changed paths, actual check results, and unverified runtime behavior. If blocked, give the exact failed command or missing prerequisite, separate baseline failures, and continue independent authorized work.
