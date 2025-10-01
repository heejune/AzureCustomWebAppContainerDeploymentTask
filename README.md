# Custom Azure Web App Container Deploy (Fork)

This repository (https://github.com/heejune/AzureCustomWebAppContainerDeploymentTask) contains a minimal fork of the Azure Pipelines task `AzureWebAppContainerV1` with a single functional addition: the `UseLinuxContainer` boolean parameter that forces Linux container handling (overriding platform detection and driving `linuxFxVersion` vs `windowsFxVersion`).

## ⚠️ Disclaimer

**This is an UNOFFICIAL fork for personal/community use.**
- ❌ Not affiliated with, endorsed by, or supported by Microsoft Corporation
- ❌ Not an official Microsoft product or service
- ✅ Derived from MIT-licensed open-source code (Microsoft's azure-pipelines-tasks)
- ✅ Provided "as-is" without warranties of any kind

Use at your own risk. For official Azure DevOps tasks, please refer to [Microsoft's official repository](https://github.com/microsoft/azure-pipelines-tasks).

## Structure
- `CustomAzureWebAppContainerDeploymentTask/` – Task implementation (TypeScript + compiled JS) and manifest-related assets.
- `vss-extension.json` – Azure DevOps extension manifest.
- `License.txt` – MIT License (original Microsoft copyright).

A more detailed task-level README is inside `CustomAzureWebAppContainerDeploymentTask/README.md`.

## Added Parameter
| Name | Type | Effect |
|------|------|--------|
| `UseLinuxContainer` | boolean | When true, overrides internal detection to treat the target as a Linux container app and apply `linuxFxVersion`. Otherwise original detection may resolve to Windows and apply `windowsFxVersion`. |

## Development
```bash
# Install deps
npm install --prefix CustomAzureWebAppContainerDeploymentTask

# Build TypeScript
npm run build --prefix CustomAzureWebAppContainerDeploymentTask

# Package extension (.vsix)
npm run package --prefix CustomAzureWebAppContainerDeploymentTask
```
The resulting `.vsix` file is created at the repository root. (VSIX files are ignored by Git.)

## Git Hygiene
- `node_modules/` excluded via `.gitignore` (installed on demand before packaging)
- `package-lock.json` is committed for reproducible builds
- No debug `console.log("DEBUG:")` statements remain
- Sensitive files (`.taskkey`, secrets) are excluded via `.gitignore`

## License & Attribution

This project is licensed under the **MIT License** (see [License.txt](License.txt)).

**Original Copyright**: © 2014 Microsoft Corporation  
**Original Source**: https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/AzureWebAppContainerV1

All third-party dependencies and their licenses are documented in [ThirdPartyNotices.txt](CustomAzureWebAppContainerDeploymentTask/ThirdPartyNotices.txt).

## Contributing

**This repository is maintained for personal use and does NOT accept external contributions.**

If you'd like to suggest improvements or report issues with the original task, please contribute to the official Microsoft repository: https://github.com/microsoft/azure-pipelines-tasks

You're welcome to fork this repository for your own modifications.
