# GitHub Cron VM Monitor

A public GitHub Pages dashboard backed by a scheduled GitHub Actions workflow.

## What it proves
- The scheduled workflow is configured to run every five minutes.
- Each workflow run provisions a fresh GitHub-hosted Ubuntu runner.
- The dashboard reads the latest workflow runs from the public GitHub Actions REST API.

## What it does NOT provide
This is **not a VPS** and must not be used as one. GitHub-hosted runners are temporary job environments and are decommissioned after the job finishes. There is no continuously running process, stable inbound IP, permanent disk, or always-available backend/API endpoint.

## View
After GitHub Pages publishes the folder:
https://l0rttt.github.io/heartbeat-vps/

## Workflow
- File: `.github/workflows/heartbeat-vps.yml`
- Schedule: every 5 minutes (UTC)
- Manual trigger: GitHub Actions > Cron VM Heartbeat > Run workflow
- Runner: `ubuntu-latest`
- Job timeout: 2 minutes

GitHub may delay or drop scheduled runs during high load. Public-repository scheduled workflows may also be automatically disabled after 60 days without repository activity. See the GitHub Actions documentation for current behavior.

## Stop
Open the Actions workflow page and choose **Disable workflow**:
https://github.com/l0rttt/l0rttt.github.io/actions/workflows/heartbeat-vps.yml

## Resume
Open the same workflow page and choose **Enable workflow**, or push a new commit affecting the workflow path.
