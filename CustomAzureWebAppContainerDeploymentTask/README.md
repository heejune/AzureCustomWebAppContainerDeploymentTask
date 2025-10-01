# Custom Azure Web App Container Deployment Task

## Overview

This project is a direct hard copy of the official Azure Pipelines task located at:
https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/AzureWebAppContainerV1

Except for the specific modifications listed below, behavior and structure are intentionally kept the same as the original task for reference and experimentation purposes.

## Modifications Added in This Fork

1. Added a new boolean task input: `UseLinuxContainer`.
2. When this flag is set, the internal logic overrides the derived `isLinuxContainerApp` value to force the task to treat the target as a Linux container app.
3. Based on that override, the task will choose to apply either `linuxFxVersion` or `windowsFxVersion` accordingly during configuration.

### UseLinuxContainer Parameter

| Parameter | Type | Default | Purpose |
|-----------|------|---------|---------|
| `UseLinuxContainer` | boolean | (implementation default) | Forces Linux container mode when true. Overrides auto-detected platform logic by setting `isLinuxContainerApp = true`, ensuring `linuxFxVersion` is used instead of `windowsFxVersion` during deployment descriptor construction. |

Internally, when `UseLinuxContainer` is enabled:
- `isLinuxContainerApp` is explicitly set (overriding any discovery logic).
- The task selects `linuxFxVersion` handling branches.
- When false (or not supplied), the original detection logic remains in effect and may result in using `windowsFxVersion` for Windows-based container targets.

No other semantic changes were introduced; all remaining code paths mirror the upstream implementation to preserve parity for troubleshooting and learning.

## Disclaimer

This code is provided strictly as a sample for reference purposes only. It is offered **without any warranties**, express or implied. No responsibility is assumed for correctness, fitness for a particular purpose, or consequences arising from its use. This fork does **not** represent or speak on behalf of Microsoft.

If you require production-grade functionality, security hardening, or official support, rely on the original, maintained Azure Pipelines tasks from the Microsoft repository.

---
*Original source: Azure Pipelines Tasks (AzureWebAppContainerV1). This fork is for educational and experimental usage.*

