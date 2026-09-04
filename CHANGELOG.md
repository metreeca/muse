# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres
to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased](https://github.com/metreeca/muse/commits/main)

### Added

- workspace scaffolding for the AI job framework: the `@metreeca/muse` core package and the `@metreeca/muse-google`
  provider package, alongside the shared build, test and documentation configuration; jobs run under the
  `@metreeca/gear` executor, which the core package brings in rather than reimplementing
