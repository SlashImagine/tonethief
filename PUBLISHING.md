# Publishing to npm

## One-time setup (5 minutes)

### 1. Create an npm account / org
Go to https://www.npmjs.com and sign up or log in.

### 2. Create an npm access token
- Go to https://www.npmjs.com → Account → Access Tokens
- Click "Generate New Token" → "Granular Access Token"
- Name: `tonethief-github-actions`
- Permissions: **Read and write** on `tonethief` package
- Copy the token

### 3. Add token to GitHub repo
- Go to https://github.com/SlashImagine/tonethief/settings/secrets/actions
- Click "New repository secret"
- Name: `NPM_TOKEN`
- Value: paste the token
- Click "Add secret"

### 4. Publish first version
```bash
# On your local machine, first time only:
npm login
npm publish --access public

# Every release after that — just tag it:
git tag v2.0.0 && git push --tags
# GitHub Actions handles the rest automatically
```

## Releasing new versions

```bash
# Bump version
npm version patch  # 2.0.0 → 2.0.1
# or
npm version minor  # 2.0.0 → 2.1.0
# or
npm version major  # 2.0.0 → 3.0.0

# Push the tag — GitHub Actions publishes automatically
git push && git push --tags
```

That's it. The workflow in `.github/workflows/publish.yml` handles everything.
