# signal-action

Sends a GitHub Actions event to signal.nick.org, authenticated with the job's
OIDC token. Only repositories of allowed owners are accepted. Never fails the
job.

```yaml
permissions:
  id-token: write
steps:
  - name: Notify
    if: always()
    uses: nkirsch/signal-action@v1
    with:
      event: deploy.${{ job.status }}
      title: example.nick.org
      message: ${{ github.ref_name }}
      url: https://example.nick.org
```

Optional `subject` and `version` default to the title and message for
`deploy.*` events; the commit SHA is always sent, and `release_url` defaults
to the GitHub release that triggered the run.

`v1` moves to the latest compatible commit.
