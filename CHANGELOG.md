# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres
to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased](https://github.com/metreeca/muse/compare/v0.1.1...HEAD)

## [0.1.1](https://github.com/metreeca/muse/compare/v0.1.0...v0.1.1) - 2026-09-09

### Changed

- requires `@metreeca/core` `^0.10.0`, `@metreeca/flow` `^0.10.0`, `@metreeca/gear` `^0.2.0` and `@metreeca/tape`
  `^0.10.1`, so that a consumer on the current line resolves one copy of each rather than a second, superseded one

## [0.1.0](https://github.com/metreeca/muse/releases/tag/v0.1.0) - 2026-09-04

Initial release, claiming the package names and enabling automated publishing. The modules carry no public API yet:
jobs run under the [@metreeca/gear](https://github.com/metreeca/gear) executor, to which this repository contributes
model services and tasks.

- `@metreeca/muse` — AI tasks and shared services
- `@metreeca/muse-google` — Google model connectors
