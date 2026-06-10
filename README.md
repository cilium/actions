# Cilium Reusable GitHub Actions

Reusable [GitHub Actions](https://docs.github.com/en/actions/sharing-automations/creating-actions/) used by the [Cilium](https://github.com/cilium/cilium) project.

## Overview

[Cilium](https://cilium.io) is an eBPF-based networking, observability, and security solution for Kubernetes. This repository contains the shared GitHub Actions that power its CI infrastructure.

## Usage


```
steps:
  - uses: cilium/actions/<action-name>@<ref>
    with:
      param: value
```


Each action directory contains an `action.yaml` (or `action.yml`) describing its inputs, outputs, and steps.

## Contributing

When adding or modifying an action:

- Pin all external action references to a full commit SHA.
- Add a `# renovate:` comment above any tool version so [Renovate](https://docs.renovatebot.com/) can keep it up to date.

## License

Apache 2.0 License. See [LICENSE](./LICENSE) for details.
