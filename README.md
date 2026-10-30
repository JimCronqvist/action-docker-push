# GitHub Action: Docker Push

Build and push a single Docker image to Github Container Registry, ghcr.io.

### Security considerations

**Only build trusted code when using credentials.**

Use credentials with the minimum required permissions. Prefer short-lived tokens over long-lived credentials, such as personal access tokens (PATs), whenever possible.

Setting `pull-requests: false` prevents Docker images from being pushed for pull requests, but **does not prevent the build itself from running**.

If build secrets are provided, a malicious Dockerfile or dependency installation script could access and potentially expose those credentials.

For this reason:

- Only run builds with secrets on trusted branches, preferably protected branches such as `master`.
- Avoid building untrusted pull requests with credentials, especially when using `pull_request_target`.
- Use tokens with the minimum permissions required, and prefer short-lived credentials.

For untrusted pull requests, use a separate workflow that builds without access to sensitive credentials.