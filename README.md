# BlinkTalk

A new Flutter project.

## CI/CD Infrastructure

This project uses a robust CI/CD pipeline built with GitHub Actions to ensure code quality, security, and consistent builds.

### 🚀 Automated Workflows

- **PR Checks (`pr-checks.yml`)**: Runs on every pull request to `main` and `develop`.
  - **Dart Format**: Ensures consistent code styling.
  - **Flutter Analyze**: Performs static analysis with strict rules.
  - **Unit Tests**: Runs tests with coverage reporting.
  - **Android Lint**: Native Android code quality checks.
  - **Kotlin Detekt**: Strict static analysis for Kotlin code.
  - **Build App Bundle**: Verifies compilation and generates a downloadable `.aab` artifact.
- **PR Metadata (`pr-metadata.yml`)**: Validates PR titles (Conventional Commits) and ensures descriptions are present.
- **SonarCloud (`sonar.yml`)**: Integrated for long-term code quality tracking and coverage visualization.
- **Security Scan (`security.yml`)**: 
  - **Gitleaks**: Detects hardcoded secrets.
  - **CodeQL**: Automated code scanning for vulnerabilities in native code.
- **Dependabot**: Automatically manages dependency updates for Flutter, Gradle, and GitHub Actions.

### 💎 Code Quality Standards

- **Strict Linting**: Custom `analysis_options.yaml` with 20+ strict rules.
- **Kotlin Quality**: Configured Detekt with custom rules for Flutter compatibility.
- **SonarCloud**: Dashboard for tracking technical debt and test coverage.

### 🛠️ Local Development

#### Git Hooks
We use a **pre-push hook** to catch issues before they reach the server. It automatically runs:
1. `flutter analyze` on changed files.
2. `detekt` on changed Kotlin files.

To set up the hook manually if it's missing:
```bash
chmod +x .git/hooks/pre-push
```

#### Code Ownership
Automated reviewer assignments are handled via `.github/CODEOWNERS`.

## Getting Started

This project is a starting point for a Flutter application.

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
