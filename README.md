# Auto-sync Issues to Project Board

Copy workflow → Add token → All issues in one place.

## Quick Start

1. **Copy workflow**: Copy `.github/workflows/auto-add-issues.yml` to **EACH repository where you create issues**
2. **Edit 2 lines**: Change `YOUR_ORG` and `PROJECT_ID` in the file  
3. **Add token**: Create token and add to repository secrets (see [SETUP.md](SETUP.md))

Done! New issues from those repositories automatically sync to your project board.

## Example

If you want issues from `my-app` and `my-docs` repos on one board:
- Copy workflow to `my-app` repository  
- Copy workflow to `my-docs` repository
- Both will send new issues to same project board

## What it does

- When issue is created → automatically adds to your project board  
- Works with private repositories
- Secure: each repository gets its own token

## Security

Each repository token can only access:
- ✅ Issues from that specific repository  
- ✅ Your organization project boards
- ❌ Cannot access other repositories

Safe to use if you trust your repository contributors.

## Need help?

See detailed setup guide: [SETUP.md](SETUP.md)