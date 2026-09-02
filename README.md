# Cilium Reusable GitHub Actions

Reusable [GitHub Actions](https://docs.github.com/en/actions/sharing-automations/creating-actions/) used by the [Cilium](https://github.com/cilium/cilium) project.

## Overview

[Cilium](https://cilium.io) is an eBPF-based networking, observability, and security solution for Kubernetes. This repository contains the shared GitHub Actions that power its CI infrastructure.

## Usage

```yaml
steps:
  - uses: cilium/actions/<action-name>@<ref>
    with:
      param: value
```

Each action directory contains an `action.yaml` (or `action.yml`) describing its inputs, outputs, and steps.

### Set commit status

The `set-commit-status` action sets the workflow's commit status on a given SHA.
The calling workflow must grant `statuses: write` permission.

```yaml
permissions:
  statuses: write

steps:
  - uses: cilium/actions/set-commit-status@<commit-sha> # main
    with:
      sha: ${{ github.sha }}
      status: pending
```

### Remove slow Azure apt mirrors

The `remove-azure-apt-mirrors` action drops the `azure.archive.ubuntu.com` entries
from `/etc/apt/apt-mirrors.txt` on GitHub-hosted Ubuntu runners, so `apt` falls back
to the official Ubuntu mirrors. It is a no-op on runners without that file.

```yaml
steps:
  - uses: cilium/actions/remove-azure-apt-mirrors@<commit-sha> # main
```

## Contributing

When adding or modifying an action:

- Pin all external action references to a full commit SHA.
- Add a `# renovate:` comment above any tool version so [Renovate](https://docs.renovatebot.com/) can keep it up to date.

## License

Apache 2.0 License. See [LICENSE](./LICENSE) for details.
