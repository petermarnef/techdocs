# Git

## Commands

|command|note
|:-|:-
|`git clean -xdf --dry-run`|removes untracked files and folders (e.g. \bin and \obj), more info on [git-clean](https://git-scm.com/docs/git-clean)
|`git reset origin/{branch}`|Reset to remote branch
|`git branch --contains {commit id}`|Search for commit in branches
|`git log {branch}..{branch} --oneline --no-merges` |Difference in commits between branches
|`git log {branch}..{branch} --pretty=format:"%h%x09%an%x09%ad%x09%s" --no-merges`|Difference in commits between branches, including date + author
|`git log | grep -B 4 -A 4 "{text to search for}"`|Show multiple lines with 'grep'

## How to

### Clone a GIT repo to a new repo in another project

1. Clone repo = `git clone <url old repo> <new name>`
2. Get remote branches locally (per branch) = `git checkout -b <local branch name> <remote branch name>` - see code below todo this step automatically (an additional pull is needed if branches already exist)
3. Set remote URL to new repo = `git remote set-url origin <url new repo>`
4. Push everything in the local repo to the remote = `git push origin --mirror`

This powershell code does a checkout of all remote branches:

``` ps
$remoteBranches = git branch -r

foreach($remoteBranch in $remoteBranches) {
    $remoteBranchFormatted = $remoteBranch.Trim()
    $localBranchFormatted = $remoteBranchFormatted.Substring($remoteBranchFormatted.IndexOf('/') + 1)

    Write-Host('Getting remote branch {0} as local branch {1}' -f $remoteBranchFormatted, $localBranchFormatted)
    git checkout -b $localBranchFormatted $remoteBranchFormatted
}
```
