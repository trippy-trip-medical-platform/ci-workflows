# Shared GitHub Actions Workflows

Reusable CI workflows for the Medical Platform monorepo.

## Available Workflows

### `spring-boot.yml` — Build & test Spring Boot services

Used by all 9 backend microservices.

**Usage in a backend repo's `.github/workflows/ci.yml`:**

```yaml
name: CI

on:
  push:
    branches: [master, main]
  pull_request:
    branches: [master, main]

jobs:
  build:
    uses: trippy-trip-medical-platform/ci-workflows/.github/workflows/spring-boot.yml@main
```

**Optional inputs:**
- `java-version` (default `'25'`)
- `run-tests` (default `true`)
- `upload-jar` (default `true`)

### `angular.yml` — Build & test Angular frontend

Used by `Medical-Frontend`.

```yaml
jobs:
  build:
    uses: trippy-trip-medical-platform/ci-workflows/.github/workflows/angular.yml@main
```

**Optional inputs:**
- `node-version` (default `'22'`)
- `legacy-peer-deps` (default `true`)
- `build-config` (default `'production'`)

## Why reusable workflows?

Without this repo, every backend would have a 45-line `ci.yml`. With it, each one is 5 lines and any CI change (e.g. JDK upgrade, new step) is a single PR here that updates all 10 services at once.
