# Setup Guide

## Step 1: Create Project Board

1. Go to your organization: `https://github.com/orgs/YOUR_ORG`
2. Click "Projects" → "New project"
3. Name it (e.g., "All Issues")
4. **Save the number** from URL: `/projects/28` → save `28`

## Step 2: Copy Workflow

Copy `.github/workflows/auto-add-issues.yml` to your repository and edit:

```yaml
# Change this line:
project-url: https://github.com/orgs/YOUR_ORG/projects/PROJECT_ID

# Example:
project-url: https://github.com/orgs/mycompany/projects/28
```

## Step 3: Create Token

1. GitHub Settings → Developer settings → Personal access tokens → **Fine-grained tokens**
2. "Generate new token"
3. **Name**: `[repo-name]-project-sync`
4. **Repository access**: Select only your repository
5. **Permissions**:
   - Repository: Issues (Read), Metadata (Read)
   - Organization: Projects (Write)
6. Generate and copy token

## Step 4: Add Token to Repository

1. Your repository → Settings → Secrets and variables → Actions
2. "New repository secret"
3. **Name**: `ADD_TO_PROJECT_PAT`
4. **Value**: Paste your token
5. "Add secret"

## Step 5: Test

Create a test issue in your repository. Check:
1. Actions tab → workflow should run ✅
2. Project board → issue should appear ✅

## Troubleshooting

**"Resource not accessible by personal access token"**
- Wrong permissions: select "Projects" not "Secrets" when creating token

**Issue not on board**
- Check Actions tab for errors
- Verify project URL is correct

**Workflow doesn't run**
- Ensure workflow file is on main branch
- Check file is exactly `.github/workflows/auto-add-issues.yml`

## Repeat for Multiple Repositories

For each additional repository:
1. Create separate token (Step 3)
2. Copy workflow file (Step 2)
3. Add token to that repository (Step 4)

**Security**: Never reuse tokens between repositories.