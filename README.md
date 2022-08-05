# github-workflows

## test.yml

Reusable workflow that launches a docker image and run CI with phpcs and phpstan checks, plus phpunit tests.

Usage:

```yaml
name: 'test'

on:
  pull_request:
    paths:
      - '**/*.php'
      - '.github/workflows/test.yml'
      - 'composer.json'
  push:
    paths:
      - '**/*.php'
      - '.github/workflows/test.yml'
      - 'composer.json'

jobs:
  test:
    uses: atlasconsulting/github-workflows/.github/workflows/test.yml@main
    with:
        app: the-app-to-test
```

## deploy.yml

Reusable workflow that launches a deploy using ansible playbook.

Usage:

```yaml
name: 'deploy'

on:
  workflow_dispatch:
    inputs:
      ansible_repo:
        description: 'the ansible repository'
        required: true
        default: 'ansible-test-repo'
        type: choice
        options:
          - ansible-test-repo
          - ansible-prod-repo
jobs:
  deploy:
    uses: atlasconsulting/github-workflows/.github/workflows/deploy.yml@main
    with:
        app: the-app-to-deploy
        ansible_repo: ${{ inputs.ansible_repo }}
```