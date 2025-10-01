# Contributing

**This repository is NOT accepting external contributions.**

This is a personal fork maintained for specific use cases. Pull requests and issues will not be reviewed or merged.

## For Contributors

If you'd like to:
- **Report bugs or suggest features for the original task**: Please contribute to the official Microsoft repository at https://github.com/microsoft/azure-pipelines-tasks
- **Make your own modifications**: Feel free to fork this repository and customize it for your needs

## For Personal Development (Repository Owner)

When making changes:
1. Install dependencies:
   ```bash
   npm install --prefix CustomAzureWebAppContainerDeploymentTask
   ```
2. Make changes (prefer updating TypeScript, then rebuild)
3. Run build & package locally:
   ```bash
   npm run build --prefix CustomAzureWebAppContainerDeploymentTask
   ```

## Guidelines
- Keep parity with upstream unless modification is clearly scoped
- Add comments where behavior diverges from the original task
- Commit the updated `package-lock.json` when dependencies change
- Avoid committing generated `.vsix` bundles or `node_modules/`

## License
All code in this repository is provided under the MIT License.
