## Mirgration of a repo
* git clone --mirror: to clone every references (commits, tags, branches)
* git push --mirror: to push everything

```
git clone --mirror https://bitbucket.org/exampleuser/repository-to-mirror.git
# Make a bare mirrored clone of the repository

cd repository-to-mirror.git
git remote set-url --push origin https://github.com/exampleuser/mirrored
# Set the push location to your mirror

git push --mirror
```

## Store credential

```
git config --global credential.helper store
```

## Find and sort files in git history

```bash
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort --numeric-sort --key=2 |
  cut -c 1-12,41- |
  $(command -v gnumfmt || echo numfmt) --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest
```

## Remove files from git history

```bash
git filter-repo --invert-paths --path <path> --force
```
Then you need to push the new histroy into the repo

```bash
git push --mirror --force
```

## Download specific directory from a Github repo

Install [GitZip for github](https://chrome.google.com/webstore/detail/gitzip-for-github/ffabmkklhbepgcgfonabamgnfafbdlkn) chrome extension

Then check the checkbox besite any directory you want to download then click the bottom right download button. 

## missing commits after rebase
[lihautan website] https://lihautan.com/commit-went-missing-after-rebase/
