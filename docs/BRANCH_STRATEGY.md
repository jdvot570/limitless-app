# Git Branch Strategy - Limitless MVP0

## Branch Structure

### Main Branches
- **`main`** - Production branch (protected)
  - Auto-deploys to production on Vercel
  - Only accepts PRs from `develop` or hotfix branches
  - Requires PR reviews and passing CI/CD

- **`develop`** - Development integration branch
  - Auto-deploys to preview environment on Vercel
  - Accepts PRs from feature branches
  - Latest development code

### Supporting Branches
- **`feature/*`** - Feature development
  - Created from `develop`
  - Merged back to `develop` via PR
  - Naming: `feature/stripe-checkout`, `feature/auth-flow`

- **`hotfix/*`** - Emergency production fixes
  - Created from `main`
  - Merged to both `main` AND `develop`
  - Naming: `hotfix/payment-bug`, `hotfix/security-patch`

## Workflow

### Feature Development
```bash
# Start new feature
git checkout develop
git pull origin develop
git checkout -b feature/your-feature

# Work on feature
git add .
git commit -m "feat: your feature description"

# Push and create PR
git push origin feature/your-feature
# Create PR to develop on GitHub
```

### Release Process
```bash
# When develop is ready for production
git checkout main
git pull origin main
git merge --no-ff develop
git push origin main
# Vercel auto-deploys to production
```

### Hotfix Process
```bash
# Create hotfix from main
git checkout main
git pull origin main
git checkout -b hotfix/critical-fix

# Fix issue
git add .
git commit -m "fix: critical issue description"

# Merge to main
git checkout main
git merge --no-ff hotfix/critical-fix
git push origin main

# Also merge to develop
git checkout develop
git merge --no-ff hotfix/critical-fix
git push origin develop

# Delete hotfix branch
git branch -d hotfix/critical-fix
```

## Vercel Integration

### Automatic Deployments
- **Production**: `main` branch → limitless.app
- **Preview**: All PRs → unique preview URLs
- **Development**: `develop` branch → dev.limitless.app (optional)

### Environment Variables
- Production: Set in Vercel project settings for `main`
- Preview: Inherit from preview environment settings
- Local: Use `.env.local` (never commit)

## Branch Protection Rules (GitHub)

### `main` branch
- ✅ Require PR reviews (1 minimum)
- ✅ Require status checks to pass
- ✅ Require branches to be up to date
- ✅ Include administrators
- ❌ Allow force pushes
- ❌ Allow deletions

### `develop` branch
- ✅ Require PR reviews (1 minimum)
- ✅ Require status checks to pass
- ❌ Allow force pushes
- ❌ Allow deletions

## Commit Message Convention

### Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting, missing semicolons, etc
- `refactor`: Code restructuring without feature changes
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `ci`: CI/CD changes

### Examples
```bash
feat(auth): add Supabase authentication flow
fix(stripe): correct VAT calculation for EU customers
docs: update README with deployment instructions
chore: update dependencies to latest versions
```

## CI/CD Pipeline

### On PR to `develop`
1. Run linting (ESLint, Prettier)
2. Run TypeScript checks
3. Run tests
4. Build project
5. Deploy preview to Vercel

### On PR to `main`
1. All checks from develop
2. Additional security scans
3. Performance checks
4. Require manual approval

## Best Practices

1. **Never commit directly to `main` or `develop`**
2. **Always use PRs for code review**
3. **Keep PRs small and focused**
4. **Update from `develop` frequently**
5. **Write descriptive commit messages**
6. **Test locally before pushing**
7. **Review Vercel preview before merging**
8. **Tag releases on `main` branch**

## Emergency Procedures

### Rollback Production
```bash
# Find last working commit
git log --oneline -10

# Revert to previous version
git checkout main
git revert HEAD
git push origin main
# Or use Vercel instant rollback feature
```

### Force Push Recovery
If someone accidentally force pushes:
1. Check Vercel deployment history
2. Use GitHub's reflog if available
3. Restore from local copies
4. Re-apply branch protection rules