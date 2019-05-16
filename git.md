# Commands
|command|note
|:-|:-
|`git clean -xdf --dry-run`|removes untracked files and folders (e.g. \bin and \obj), more info on [git-clean](https://git-scm.com/docs/git-clean)

# How to
## Clone a GIT repo to a new repo in another project
1. Clone repo = `git clone <url old repo> <new name>`
2. Get remote branches locally (per branch) = `git checkout -b <local branch name> <remote branch name>` - see code below todo this step automatically (an additional pull is needed if branches already exist)
3. Set remote URL to new repo = `git remote set-url origin <url new repo>`
4. Push everything in the local repo to the remote = `git push origin --mirror`

This code does a checkout of all remote branches:

``` ps
$remoteBranches = git branch -r

foreach($remoteBranch in $remoteBranches) {
    $remoteBranchFormatted = $remoteBranch.Trim()
    $localBranchFormatted = $remoteBranchFormatted.Substring($remoteBranchFormatted.IndexOf('/') + 1)

    Write-Host('Getting remote branch {0} as local branch {1}' -f $remoteBranchFormatted, $localBranchFormatted)
    git checkout -b $localBranchFormatted $remoteBranchFormatted
}
```