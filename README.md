# adp-devsite-workflow
A collection of common workflows to be used by repos that deal with developer.adobe.com

## Cache-clearing file lists

`deploy-v2.yml` reads cache-clearing file lists from JSON files under the runner's
temporary `devsite-cache-files` directory, keeping large arrays out of the
`actions/github-script` input. Incremental cache clearing uses a separate
changed-files invocation with file-safe JSON escaping; full enumeration writes
`all_files.json` while retaining its existing deployment output. Missing files
or invalid JSON fail cache clearing rather than silently skipping files.

Only the stage and production cache-clearing steps use this file-based transport.
Deployment steps retain their existing inline arrays and size limits. Caller
inputs, conditions, preview/live ordering and cache environment routing are unchanged.
