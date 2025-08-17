# Git Workflow and Configuration Guide

## Repository Setup Information

### Primary Repositories
1. **Development Repository** (THIS REPO)
   - **URL**: https://github.com/Dfunk55/turbo-loader
   - **Purpose**: Ongoing development, future versions, R&D
   - **Local Path**: `F:\Development\02_ACTIVE_DEVELOPMENT\TTRPG_Suite\turbo-loader-dev\`

2. **Commercial Repository**
   - **URL**: https://github.com/Dfunk55/turbo-loader-v3
   - **Purpose**: v3.0.0 production release, commercial materials
   - **Local Path**: `F:\Development\05_Deployment_Ready\turbo_loader_dd\`

### Git Configuration

#### Required User Configuration
```bash
git config user.name "Dustin Painter"
git config user.email "djpainter1105@gmail.com"
```

#### GitHub Authentication
```bash
# Auth token location
F:\.env (GITHUB_TOKEN variable)

# Login command
gh auth login --with-token < F:\.env
```

## Commit Standards

### Commit Message Format
```
<type>: <short description>

<detailed body explaining what was changed and why>

Technical details:
- Specific changes made
- Files affected
- Testing performed

Generated with Claude Code (https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

### Commit Types
- **feat**: New feature development
- **fix**: Bug fixes and error corrections
- **test**: Testing framework improvements
- **docs**: Documentation updates
- **refactor**: Code restructuring without functionality changes
- **build**: Build system and dependency changes
- **ci**: Continuous integration pipeline changes
- **release**: Version releases and commercial packages

### Example Commit Messages

#### Feature Development
```
feat: Add enhanced memory optimization algorithm

Implemented new caching system that reduces memory usage by 35%
during asset loading operations. This builds on the existing 60%
speed improvements.

Technical details:
- Modified core loading algorithms in plugin/main.gd
- Added memory monitoring in installer/optimization.py
- Updated test suite to validate memory improvements
- All tests passing (100% coverage maintained)

Generated with Claude Code (https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

#### Bug Fix
```
fix: Resolve Unicode encoding issues in Windows installer

Fixed 'charmap' codec errors that occurred during installation on
Windows systems when processing files with Unicode characters.

Technical details:
- Replaced all Unicode characters with ASCII equivalents
- Updated encoding handling in installer scripts
- Tested on Windows 10 and Windows 11
- Docker tests passing on all platforms

Generated with Claude Code (https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

#### Documentation Update
```
docs: Add complete project context for future development

Created comprehensive documentation including project history,
technical specifications, and all information needed for
development without previous conversation context.

Technical details:
- Added PROJECT_CONTEXT.md with complete project overview
- Updated README.md with current status
- Created GIT_WORKFLOW.md for future reference
- All documentation reflects v3.0.0 production status

Generated with Claude Code (https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

## Branch Strategy

### Main Branch
- **Branch**: `master`
- **Purpose**: Stable development code
- **Protection**: All commits should be tested before pushing

### Feature Development
```bash
# Create feature branch
git checkout -b feature/memory-optimization

# Work on feature
# ... make changes ...

# Commit changes
git add -A
git commit -m "feat: Add memory optimization feature"

# Merge back to master
git checkout master
git merge feature/memory-optimization

# Push to origin
git push origin master
```

### Release Process
```bash
# Create release branch
git checkout -b release/v4.0.0

# Finalize release materials
# ... prepare commercial package ...

# Tag release
git tag -a v4.0.0 -m "Release version 4.0.0 - Enhanced memory optimization"

# Push release
git push origin release/v4.0.0
git push origin v4.0.0
```

## Pre-Commit Checklist

### Development Repository
- [ ] All tests passing (`pytest testing/`)
- [ ] Code formatted (`black .`)
- [ ] Linting clean (`flake8 .`)
- [ ] Documentation updated
- [ ] No Unicode characters in Python files
- [ ] Requirements.txt updated if dependencies changed

### Commercial Repository
- [ ] E2E testing completed
- [ ] Docker tests passing
- [ ] Commercial package tested
- [ ] Documentation updated
- [ ] Version numbers consistent
- [ ] Quality assurance checklist completed

## Common Git Commands

### Repository Setup
```bash
# Clone development repo
git clone https://github.com/Dfunk55/turbo-loader.git
cd turbo-loader

# Configure user
git config user.name "Dustin Painter"
git config user.email "djpainter1105@gmail.com"

# Verify remote
git remote -v
```

### Daily Workflow
```bash
# Check status
git status

# Add files
git add -A

# Commit with proper message
git commit -m "type: description"

# Push to GitHub
git push origin master
```

### Repository Maintenance
```bash
# Check for uncommitted changes
git status

# View recent commits
git log --oneline -10

# Check remote status
git remote show origin

# Pull latest changes
git pull origin master
```

## File Management

### What to Include in Development Repo
- ✅ Source code and scripts
- ✅ Testing framework
- ✅ Documentation
- ✅ Requirements and dependencies
- ✅ Build tools and automation

### What to Exclude (in .gitignore)
- ❌ Commercial packages (`commercial_package/`)
- ❌ Build artifacts (`*.exe`, `*.zip`)
- ❌ Environment files (`.env`)
- ❌ Temporary files (`*.tmp`, `temp/`)
- ❌ IDE files (`.vscode/`, `.idea/`)
- ❌ Python cache (`__pycache__/`)

### What to Include in Commercial Repo
- ✅ Production packages
- ✅ Marketing materials
- ✅ Legal documents
- ✅ Sales resources
- ✅ Quality assurance reports
- ✅ Customer-facing documentation

## Troubleshooting

### Common Issues and Solutions

#### Authentication Problems
```bash
# Re-authenticate with GitHub
gh auth login --with-token < F:\.env

# Verify authentication
gh auth status
```

#### Git Lock Files
```bash
# Remove lock file if git process crashed
rm .git/index.lock
```

#### Large Repository Issues
```bash
# If repository is too large, exclude large files
git rm --cached large_file.zip
echo "large_file.zip" >> .gitignore
git commit -m "Remove large file from tracking"
```

#### Unicode Encoding Issues
```bash
# Check for Unicode characters
grep -P '[^\x00-\x7F]' *.py

# Replace Unicode with ASCII equivalents
# Manual replacement required
```

## Repository Synchronization

### Keeping Repositories in Sync
```bash
# Development repo workflow
cd F:\Development\02_ACTIVE_DEVELOPMENT\TTRPG_Suite\turbo-loader-dev\
git add -A
git commit -m "feat: new development feature"
git push origin master

# Commercial repo workflow (when ready for release)
cd F:\Development\05_Deployment_Ready\turbo_loader_dd\
git add -A
git commit -m "release: v4.0.0 commercial package"
git push origin master
```

### Cross-Repository References
- Always reference related repository in commit messages
- Maintain version consistency between repositories
- Update documentation in both repositories when applicable

---

**This guide provides complete Git workflow information for future development without previous context.**