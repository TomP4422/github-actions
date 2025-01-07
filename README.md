# GitHub Actions for CI/CD

This project demonstrates the implementation of a CI/CD pipeline using GitHub Actions to ensure quality and automate deployment for a fullstack web application. The pipeline is set up to:

1. Run Cypress component tests for any pull request (PR) targeting the `develop` branch.
2. Automatically deploy the application to Render when the `develop` branch is merged into the `main` branch.

## Features

- **Continuous Integration:** Validates code changes by running tests on PRs to the `develop` branch.
- **Continuous Deployment:** Deploys the application to Render when changes are merged into the `main` branch.
- **Fullstack Application:** Includes both client and server components.

## Repository Structure

- `client/` - Frontend application built with modern frameworks.
- `server/` - Backend application with APIs and database integrations.
- `cypress/` - Contains Cypress test configurations and test files.
- `cypress.config.ts` - Configuration file for Cypress testing.
- `.gitignore` - Specifies files and folders to ignore in version control.
- `package.json` - Contains dependencies and scripts for the project.
- `vite.config.ts` - Configuration for the Vite build tool.

## Prerequisites

1. **Render Deployment Setup:**
   - Deploy the application manually to Render.
   - Disable Auto-Deploy and copy the `Deploy Hook` URL.

2. **GitHub Secrets Configuration:**
   - Add the following secrets to your repository:
     - `RENDER_DEPLOY_HOOK`: The Deploy Hook URL from Render.
     - `RENDER_API_KEY`: Your Render API key.

3. **Branch Structure:**
   - Use a `develop` branch for staging changes.
   - Merge feature branches into `develop`.
   - Merge `develop` into `main` for production deployment.

## CI/CD Workflow

### 1. Test Workflow

- **Trigger:** Pull Request to `develop` branch.
- **Action:**
  - Install dependencies.
  - Run Cypress component tests.
  - Display test results in the GitHub Actions tab.
- **YAML File:** Located in `.github/workflows/test.yml`.

### 2. Deployment Workflow

- **Trigger:** Merge from `develop` to `main` branch.
- **Action:**
  - Trigger a deployment to Render using the Deploy Hook.
  - Ensure successful deployment of the application.
- **YAML File:** Located in `.github/workflows/deploy.yml`.

## Scripts

Use the following scripts defined in `package.json`:

- `npm run test`: Runs the Cypress tests.
- `npm start`: Starts the application.
- `npm build`: Builds the application for production.

## How to Use

1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create feature branches for new changes and make PRs to the `develop` branch.

4. Ensure Cypress tests pass before merging the PR.

5. Merge `develop` into `main` for deployment.

## References

- [Render Deploy Hooks](https://docs.render.com/deploy-hooks)
- [GitHub Secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions)
- [Cypress Documentation](https://docs.cypress.io/)

## License

This project is licensed under the [MIT License](LICENSE).

