`git config --global user.name "Your Name" && git config --global user.email "your.email@example.com"` - Initial setup (name and email).
`git clone https://github.com/user/repo.git` - Clone a repository from GitHub.
`git status` - Check current branch and file changes.
`git add .` - Stage all modified files.
`git commit -m "message"` - Commit staged changes.
`git checkout -b feature-name` - Create and switch to a new branch.
`git push -u origin branch-name` - Push branch to GitHub.
`git pull origin branch-name` - Get latest changes from remote branch.
`git log` - View commit history.
`git restore filename` - Discard changes in a file.

# Details
## Initial Setup
`git config --global user.name "Your Name"` - Set your name globally.
`git config --global user.email "your.email@example.com"` - Set your email globally.
`git config --global github.token "your_token"` - Set GitHub personal access token (generate at https://github.com/settings/tokens).

## Repository Basics
`git init` - Initialize a new local repository.
`git clone https://github.com/user/repo.git` - Clone a repository from GitHub.
`git status` - Show current branch, staged/unstaged changes, and untracked files.
`git log` - Display commit history.
`git log -n 5` - Show last 5 commits.

## Tracking Changes
`git add filename` - Stage a specific file.
`git add .` - Stage all modified and new files.
`git commit -m "message"` - Commit staged changes with a message.
`git commit -am "message"` - Stage all modified files and commit in one command.
`git diff` - Show unstaged changes.
`git diff --staged` - Show staged changes.

## Branches
`git branch` - List local branches.
`git branch -a` - List all branches (local and remote).
`git branch feature-name` - Create a new branch.
`git checkout -b feature-name` - Create and switch to a new branch.
`git checkout branch-name` - Switch to an existing branch.
`git branch -d branch-name` - Delete a local branch.
`git push -u origin branch-name` - Push branch to GitHub and set upstream tracking.
`git push origin branch-name` - Push branch to GitHub.
`git pull origin branch-name` - Fetch and merge remote branch changes.

## Pull Request Workflow
1. `git checkout -b feature/your-feature` - Create feature branch.
2. Make changes and commit: `git add . && git commit -m "your message"`.
3. `git push -u origin feature/your-feature` - Push to GitHub.
4. Go to GitHub and create PR.
5. Address review feedback: make changes, commit, and push again.
6. Merge on GitHub when approved.
7. `git checkout main && git pull origin main && git branch -d feature/your-feature` - Switch to main, pull latest, delete local branch.

## Merge Conflicts
`git status` - Identify files with conflicts (marked as "both modified").
`git diff` - View conflict details (<<<<<<, =======, >>>>>> markers).
Manually edit conflicted files, keep desired code, remove markers.
`git add resolved-file` - Stage resolved file.
`git commit -m "Resolve merge conflicts"` - Complete the merge.
`git merge --abort` - Cancel merge and return to pre-merge state.

## Undoing Changes
`git restore filename` - Discard changes in a file (reverts to last commit).
`git restore --staged filename` - Unstage a file (keep changes).
`git reset --soft HEAD~1` - Undo last commit, keep changes staged.
`git reset --hard HEAD~1` - Undo last commit, discard all changes.
`git reflog` - View history of HEAD movements (recover deleted commits).

## Verification
`git config --global --list` - Display all global configuration settings.
`git log --oneline` - Show commit history in compact format.
