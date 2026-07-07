# BlinkTalk

A professional Flutter project with high-grade CI/CD and DevOps automation.

## 🚀 DevOps Infrastructure (12 Phases)

This project implements a complete, industry-standard automation pipeline using GitHub Actions, Fastlane, and SonarCloud.

### 📋 Automated Workflows

1. **PR Checks (`pr-checks.yml`)**: Parallel validation for every Pull Request.
   - **Dart Format**: UI/Code styling.
   - **Flutter Analyze**: Strict static analysis.
   - **Unit Tests**: Logic validation with coverage.
   - **Android Lint**: Native Android quality checks.
   - **Kotlin Detekt**: Strict Kotlin static analysis.
   - **Build App Bundle**: Generates optimized `.aab` artifacts.
2. **PR Metadata (`pr-metadata.yml`)**: Validates titles (Conventional Commits) and descriptions.
3. **Automated Versioning (`release-please.yml`)**: Manages `pubspec.yaml` versions and `CHANGELOG.md` automatically.
4. **Security Scan (`security.yml`)**: 
   - **Gitleaks**: Secrets detection.
   - **CodeQL**: Deep vulnerability scanning for native code.
5. **SonarCloud (`sonar.yml`)**: Continuous quality gate and coverage dashboard.
6. **Release Pipeline (`release.yml`)**: Single-command production deployment triggered by tags.

### 💎 Code Quality & Standards

- **Strict Linting**: Comprehensive `analysis_options.yaml` (20+ rules).
- **Kotlin Standard**: Custom Detekt configuration for Flutter compatibility.
- **SonarCloud**: Unified dashboard for technical debt and coverage.
- **Code Ownership**: Automated reviewer assignments via `.github/CODEOWNERS`.

---

## 🔑 Setup & Secrets Management

To enable full automation, you must configure the following in your GitHub Repository Secrets.

### 1. SonarCloud
- `SONAR_TOKEN`: Your project analysis token.

### 2. Android App Signing
Required for signed production builds.
- `ANDROID_KEYSTORE_BASE64`: Base64 of your `.jks` file (`openssl base64 -A -in upload-keystore.jks`).
- `KEY_ALIAS`: Your key alias (default: `upload`).
- `KEY_PASSWORD`: Password for the key.
- `STORE_PASSWORD`: Password for the keystore.

### 3. Google Play Store
- `PLAYSTORE_SERVICE_ACCOUNT_JSON`: The full JSON from your Google Cloud Service Account (Release Manager role).

---

## 🛠️ Developer Guide

### Local Automation
Every push is locally verified to ensure no "dirty" code reaches the server.
```bash
# Setup the pre-push hook if not active
chmod +x .git/hooks/pre-push
```

### How to Release (The "One-Command" Flow)
1. Use **Conventional Commits** (`feat:`, `fix:`, `chore:`, etc.).
2. Merge `develop` into `main`.
3. **Release Please** creates a "Release PR". Merge it.
4. Run the magic command:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
5. GitHub Actions will automatically **Test -> Lint -> Sonar -> Build -> Sign -> Upload to Play Store (Internal Testing)**.

---

## Getting Started

This project is a starting point for a Flutter application.

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
