# adp-devsite-workflow
A collection of common workflows to be used by repos that deal with developer.adobe.com

## Deployment file lists

`deploy-v2.yml` stores file lists as JSON under the runner's temporary directory.
Incremental deployments use the changed-files action's `all_changed_files.json`
and `deleted_files.json`; full deployments write `all_files.json`. Deployment and
cache steps read these files at runtime instead of embedding large arrays in
action scripts or environment variables, avoiding process-launch size limits.
Missing files or invalid JSON fail the step rather than silently skipping files.
Caller workflow inputs and deployment behavior remain unchanged.
