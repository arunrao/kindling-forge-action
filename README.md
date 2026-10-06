# Kindling Forge runner

The GitHub Action that Kindling's Forge workflow runs. It claims a build job from your Kindling server, lets a coding agent work in a branch of your repository, runs your tests, and opens a pull request. A human always merges.

This repository holds only the built action (`action.yml` and `dist/index.js`). It is published so that any repository can use it: GitHub only lets a workflow load an action from a private repository when both repositories are private and share an owner.

## Use

Kindling writes this workflow for you (Board Settings, Agent factory, Install workflow). The step that loads this action is:

```yaml
- uses: arunrao/kindling-forge-action@forge-v1
  with:
    job_id: ${{ github.event.inputs.job_id }}
    kindling_url: https://your-kindling.example.com
    mode: ${{ github.event.inputs.mode }}
```

Pin to a commit SHA instead of the tag if you want to review each update before it runs with write access to your repository.

## What it does and does not hold

It holds no secrets. Credentials arrive at run time from your Kindling server, for one job at a time, and the server does not trust the runner's own account of what it spent.
