# Dual Repository Setup

This website is deployed on **two separate GitHub Pages repositories** with identical content but different custom domains:

## Repositories
1. **MatiasDurruty.github.io**
   - Domain: cv.matiousp.fr
   - Location: `/home/matiasdu/git_local/misc/static_website/MatiasDurruty.github.io`
   - Remote: `git@github-larrart:MatiasDurruty/MatiasDurruty.github.io`

2. **matious-site**
   - Domain: matious.fr
   - Location: `/home/matiasdu/git_local/misc/static_website/matious-site`
   - Remote: `git@github-larrart:MatiasDurruty/matious-site`

## Important: Syncing Changes

**ALL website modifications must be applied to BOTH repositories** to keep the content identical.

### Workflow for changes:
1. Make changes in one repository (e.g., MatiasDurruty.github.io)
2. Copy the modified files to the other repository (e.g., matious-site)
3. Commit and push changes to both repositories
4. **Exception**: Keep CNAME files different (cv.matiousp.fr vs matious.fr)

### Quick sync command example:
```bash
# After making changes in MatiasDurruty.github.io
cp -r /home/matiasdu/git_local/misc/static_website/MatiasDurruty.github.io/{index.html,styles.css,script.js,translations.js,README.md,images} /home/matiasdu/git_local/misc/static_website/matious-site/

# Then commit and push in matious-site
cd /home/matiasdu/git_local/misc/static_website/matious-site
git add .
git commit -m "Sync changes from MatiasDurruty.github.io"
git push
```

## SSH Configuration
Both repositories use the **github-larrart** SSH host configuration which authenticates with:
- Email: matias.larrart@gmail.com
- SSH Key: ~/.ssh/github_larrart

**Never use gh CLI** as it authenticates with the DataDome GitHub account.
