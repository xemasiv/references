# references

## Minimal Dev Env (Win64)

#### Google Chrome
* @ https://www.google.com/chrome/?system=true&standalone=1

#### Gtools
* @ http://p-nand-q.com/download/gtools/index.html
* **pathed** (for appending paths to PATH)
  * Append current path: `pathed /APPEND %CD% /MACHINE`
  * Append specific path: `pathed /APPEND C:\path\goes\here /MACHINE`
* **which** (for locating files)
  * Usage: `which calc`
  * Returns: `C:\Windows\system32\calc.exe`

#### SysInternals Suite (binaries only)
* @ https://technet.microsoft.com/en-us/sysinternals/bb842062.aspx

#### Curl (binaries only)
* @ https://curl.haxx.se/download.html (Viktor Szakáts' release)

#### Cmder
* @ http://cmder.net/

#### Cygwin (bash-based)
* @ https://cygwin.com/install.html
* Note: Select `git`, `wget`, `openssh`, `bash-completion` and `chere` (required for cmder)
* Comes with `bash`, `utils-linux`, `openssl`
* Setup with `cmder` as a task:
  * Task name (1st input, text-box): `cygwin`
  * Task parameters (2nd input, text-box): `/icon C:\cygwin64\Cygwin-Terminal.ico`
  * Commands (3rd input, text-area): `C:\cygwin64\Cygwin.bat -c "/bin/xchere /bin/bash.exe '%V'"`
  * Add hotkey: `CTRL + N`
  * `Save Settings`
* Append to path with `pathed`:
  * Open `cmd` as Admin
  * Go to `C:\cygwin64\bin`
  * Run `pathed /APPEND %CD% /MACHINE`

#### Putty
* @ http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

#### WinSCP
* @ https://winscp.net/eng/download.php

#### 7-zip
* @ https://www.7-zip.org/download.html

#### Atom Editor
* @ https://atom.io

#### Notepad++
* @ https://notepad-plus-plus.org/download/v7.5.6.html

#### Java
* @ https://www.java.com/en/download/manual.jsp

#### SumatraPDF
* @ https://www.sumatrapdfreader.org/download-free-pdf-viewer.html

#### K-Lite Codec Pack
* @ https://www.codecguide.com/download_kl.htm

#### F.lux
* @ https://justgetflux.com

#### OpenSSH (optional, for cmd)
* @ https://www.mls-software.com/opensshd.html

#### Git (optional, for cmd)
* @ https://git-scm.com/download/

#### Git Flow
* Setup
  * At `cygwin` terminal, just run:
  ```
  wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
  ```
* Refs:
  * https://github.com/nvie/gitflow
  * https://nvie.com/posts/a-successful-git-branching-model/
  * https://jeffkreeftmeijer.com/git-flow/
  * https://github.com/nvie/gitflow/wiki/Windows

---

## Atom

* Basics
  * Font: `Operator Mono Light` (Operator Mono Family)
  * Syntax Theme: `monokai-shade`
  * UI Theme: `City Lights`
  * Icon theme: `city-lights-icons`
* Packages
  * `language-babel`
  * `linter-flow` (for Facebook flow types)
  * `busy-signal`
  * `minimap`
  * `linter-eslint` (for Airbnb javascript style guide)

## Airbnb Javascript Style Guide
* Install babel preset
  * Install with yarn
  ```
  yarn add -D babel-preset-airbnb
  ```
  * Modify `.babelrc`
  ```
  {
    "presets": ["airbnb"]
  }
  ```
  ```
  // when replacing preset env
  {
    "presets": [["airbnb", {
      "targets": {
        "chrome": 50,
        "explorer": 11,
        "firefox": 45
      }
    }]]
  }
  ```
* Follow https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb
  * List peer dependencies:
  ```
  npm info "eslint-config-airbnb@latest" peerDependencies
  ```
  * Add each peer dependency:
  ```
  yarn add -D <dependency1>@<version> <dependency2>@<version> <dependency3>@<version>
  ```
  * Add `eslint` & `eslint-config-airbnb` itself:
  ```
  yarn add -D eslint eslint-config-airbnb
  ```
  * Create `.eslintrc.js` file:
  ```
  module.exports = {
    "extends": "airbnb"
  };
  ```
  * Install `linter-eslint` on Atom Editor
  * Install `babel-eslint`
  ```
  yarn add babel-eslint -D
  ```
  * Modify `.eslintrc`
  ```
  module.exports = {
    "parser": "babel-eslint" ,
    "rules": {
      "strict": 0
    },
    "extends": "airbnb"
  };
  ```

## Facebook Flow
* Installation
  * Install `babel-cli` and `babel-preset-flow`
  ```
  yarn add -D babel-cli babel-preset-flow
  ```
  * Add `flow` in `.babelrc` file:
  ```
  {
    "presets": ["flow"]
  }
  ```
  * Add `flow` bin:
  ```
  yarn add --dev flow-bin
  ```
  * Run `flow`
  ```
  yarn run flow
  ```
  * Install `linter-flow` on Atom Editor

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
