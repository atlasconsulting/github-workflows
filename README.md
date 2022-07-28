# github-workflows

## php-ci-cs-stan.yml

Reusable workflow that launches a docker image and run CI with phpcs and phpstan checks.

Usage example of caller workflow:

```yaml
name: 'php'

on:
  pull_request:
    paths:
      - '**/*.php'
      - '.github/workflows/php.yml'
      - 'composer.json'
  push:
    paths:
      - '**/*.php'
      - '.github/workflows/php.yml'
      - 'composer.json'

jobs:
  call:
    uses: atlasconsulting/github-workflows/.github/workflows/php-cs-stan.yml@main
```