# Branching Strategy

This document outlines the branching and workflow strategy for the project.

## Branch Types
- **main/master**:  
  - Production-ready master code.  
  - Protected branch (requires PR review before merging).  

- **develop**:  
  - Active development branch.  
  - Integration of all features before release.  

- **feature/**:  
  - Each new feature or task gets its own branch.  
  - Naming convention: `feature/<short-description>`  
  - Example: `feature/user-authentication`

- **release/**:  
  - Pre-release staging and final testing.  
  - Naming convention: `release/<short-description>`  
  - Example: `release/sprint1`

- **hotfix/**:  
  - For urgent fixes on production.  
  - Naming convention: `hotfix/<issue-description>`  

## Workflow
1. Clone the repo
  git clone https://github.com/13parTha/ABB_interview.git
  cd ABB_interview
2. Create a feature branch
  git checkout develop
  git checkout -b feature/login-api
3. Commit & Push
  git add .
  git commit -m "Add login API"
  git push origin feature/login-api
4. Open a Pull Request
  Merge feature/* -> develop
  Merge release/* -> main & develop
  Merge hotfix/* -> main & develop

## Release Process
1. Create a release branch from develop
  git checkout develop
  git checkout -b release/v1.0.0
2. Final Testing & version bump
3. Merge into main & tag
  git checkout main
  git merge release/v1.0.0
  git tag -a v1.0.0 -m "Release v1.0.0"
  git push origin main --tags
4.Merge back to develop
  git checkout develop
  git merge release/v1.0.0

## Hotfix Process
1. Create hotfix branch from main
  git checkout main
  git checkout -b hotfix/critical-bug
2. Fix,test & commit
3. Merge into main & tag
  git checkout main
  git merge hotfix/critical-bug
  git tag -a v1.0.1 -m "Hotfix v1.0.1"
  git push origin main --tags
4. Merge into Develop
  git checkout develop
  git merge hotfix/critical-bug
