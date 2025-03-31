# 📦 Build & Push Docker Image to GHCR

This GitHub Action builds your Docker image and pushes it to GitHub’s Container Registry (GHCR).

---

## ✨ Features

- Multi-platform builds (AMD64 + ARM64)
- Pushes to GHCR with latest and commit SHA tags
- Triggers automatically on commit with `docker:build`
- Supports manual trigger via GitHub UI

---

## ⚖️ Configuration

### 1. Set Your Dockerfile Path

Update the environment variable at the top of `.github/workflows/docker-build.yml`:

```yaml
env:
  DOCKERFILE_PATH: path/to/your/Dockerfile
```

---

## 🚀 How to Trigger a Build

### Option 1: Commit with a Special Message

Push your code with a commit message that includes:

```
docker:build added new features
```

### Option 2: Run It Manually

1. Go to the **Actions** tab
2. Select the **"Build & Push Docker Image to GHCR"** workflow
3. Click **"Run workflow"**

---

## 🔁 Tags

Two tags will be created:

- `:latest` — always points to the newest successful build
- `:<commit SHA>` — unique version for reference

---

## 🔐 Secrets

You will need to create a **Personal Access Token (PAT)**:

### ✨ How to Create a PAT for GHCR

1. Go to [GitHub Developer Settings](https://github.com/settings/tokens)
2. Click **"Generate new token (classic)"**
3. Check the following scopes:
   - `write:packages`
   - `read:packages`
   - `repo` (only if pushing from a private repo)
4. Generate the token and copy it
5. Add it as a secret named `GHCR_PAT` in your repository
