# references
Let's keep it simple.


## Atom

* Basics
  * Font: `Operator Mono`
  * Syntax Theme: `monokai-shade (themes)`
  * UI Theme: `One Dark (themes)`
  * Icon theme: `city-lights-icons (packages)`
* Packages
  * `language-babel`
  * `linter-flow`
  * `busy-signal`
  * `minimap`

## Git

* Basics
  * Config
  ```
  git config --global user.name “xemasiv”
  git config --global user.email “xemasiv@gmail.com”
  ```
  * Init
  ```
  git init
  ```
  * Status
  ```
  git status
  ```
  * Commits
  ```
  git add -A && git commit -m "Message goes here"
  ```
  * Diffing files
  ```
  git diff filename
  git diff --stat filename
  ```
  * Undoing changes to `HEAD`:
  ```
  git reset --hard HEAD
  ```
* Branching
  * Check current branch:
  ```
  git branch
  ```
  * Create branch `dev` & checkout branch `dev`
  ```
  git branch dev && git checkout dev
  ```
  * Auto-create, and checkout branch `experiment`
  ```
  git checkout -b experiment
  ```
* Merging
  * Commit changes in `experiment` branch:
  ```
  git add -A && git commit -m "Experiment complete."
  ```
  * Switch to `dev` branch:
  ```
  git checkout dev
  ```
  * Merge `experiment` branch with `dev` branch:
  ```
  git merge experiment
  ```
  * Delete `experiment` branch:
  ```
  git branch -d experiment
  ```
* Rebasing
  * Create `experiment` branch:
  ```
  git checkout -b experiment
  ```
  * Commit changes in `experiment` branch:
  ```
  git add -A && git commit -m "Experiment complete."
  ```
  * Move to `dev` branch and rebase:
  ```
  git rebase experiment
  ```
  * Delete `experiment` branch:
  ```
  git branch -d experiment
  ```
  * Helpers:
  ```
  git rebase --continue
  git rebase --abort
  git rebase --skip
  ```
* Remotes
  * Add
  ```
   git remote add origin git://github.com/..
  ```
  * Push
  ```
  git push -u origin master
  ```
  * Pull
  ```
  git pull
  ```
