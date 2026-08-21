# If you want to contribute and create a pull request, these are the step by step procedure for new comers.

## 1. Fork the repository

Go to:

vimpostor/vim-tpipeline on GitHub

Click Fork → create the fork under your GitHub account

## 2. Clone your fork

```bash
git clone https://github.com/YOUR_USERNAME/vim-tpipeline.git
cd vim-tpipeline
```
add the original repository as `upstream`:

```bash
git remote add upstream <link-to-original-repo>
```
verify:

```bash
git remote -v
```
## 3. Create a specific named branch for the fix

Don't make your changes directly on master/main.

```bash
git checkout -b specific-fix-name-as-branch
```

## 4. Apply your fixes

Edit: fixable file with the fix

then after saving 

```bash
git diff
```
make sure only intended changes are present.

## 5. Test

```bash
git status
```
Then commit and push into upstream repo:

```bash 
git add /path/to/fixed/file
git commit -m "fixed"

# this specific command is to push to your fork to compare and PR
git push -u origin specific-fix-name-as-branch
```

## 7. Create the pull request

You should see a Compare & pull request button for your newly pushed branch.

You need to make sure the repositories/branches are:
base repository:   original/repository
base branch:       (whatever the repository currently uses)

head repository:   YOUR_USERNAME/forked_repo
compare branch:    specific-fix-name-as-branch

The important part is that base = original repository and compare/head = your fork's branch.

## 8. Small parts
PR title, PR description, ISSUE number (e.g #79 and in the issue update it with updated PR number #123)

>[!TIP] 
> If you want to maintainers to edit slightly your changes directly to your forked branch then tick the **Allow edits from maintainers** if available.
