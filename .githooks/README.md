# Git hooks

Activate the repository hooks in each clone:

```sh
git config --local core.hooksPath .githooks
```

The pre-push hook checks the author, committer, and full message of each outgoing commit for `Claude` or `Codex` (case insensitive), including co-author trailers. It rejects the push if either name appears. It does not inspect file contents or commits already on the destination branch.
