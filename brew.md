# brew 

[TOC]
## man

### outdated formulaes & casks

```bash
antonio@Antonios:~$ brew outdated -v | grep -v '\[pinned at .*\]'
```





### cleanup [*`options`*] [*`formula`*|*`cask`*]

**Description** : Remove stale lock files and outdated downloads for all formulae and casks, and remove old versions of installed formulae. If arguments are specified, only do this for the given formulae and casks. Removes all downloads more than 120 days old. This can be adjusted with `HOMEBREW_CLEANUP_MAX_AGE_DAYS`.

  - `--prune`: Remove all cache files older than specified *`days`*.
  - `-n`, `--dry-run`: Show what would be removed, but do not actually remove anything.
  - `-s`: Scrub the cache, including downloads for even the latest versions. Note downloads for any installed formulae or casks will still not be deleted. If you want to delete those too: `rm -rf "$(brew --cache)"`
  - `--prune-prefix`: Only prune the symlinks and directories from the prefix and remove no other files.

  

### list _formulae_

**Description** : Confirm the details about the package.

**e.g : ** 

```bash
antonio@Antonios:~$ brew list zsh
/usr/local/Cellar/zsh/5.8/bin/zsh
/usr/local/Cellar/zsh/5.8/bin/zsh-5.8
/usr/local/Cellar/zsh/5.8/lib/zsh/ (36 files)
/usr/local/Cellar/zsh/5.8/share/info/ (8 files)
/usr/local/Cellar/zsh/5.8/share/man/ (17 files)
/usr/local/Cellar/zsh/5.8/share/zsh/ (1462 files)
```

### info [_options_] [_formula_]

**Description** : Display brief **statistics** for your Homebrew installation.

If *`formula`* is provided, show summary of information about *`formula`*.

  - `--analytics`: List global Homebrew analytics data or, if specified, installation and build error data for *`formula`* (provided neither `HOMEBREW_NO_ANALYTICS` nor `HOMEBREW_NO_GITHUB_API` are set).
  - `--days`: How many days of analytics data to retrieve. The value for *`days`* must be `30`, `90` or `365`. The default is `30`.
  - `--category`: Which type of analytics data to retrieve. The value for *`category`* must be `install`, `install-on-request` or `build-error`; `cask-install` or `os-version` may be specified if *`formula`* is not. The default is `install`.
  - `--github`: Open the GitHub source page for *`formula`* in a browser. To view formula history locally: `brew log -p` *`formula`*
  - `--json`: Print a JSON representation of *`formula`*. Currently the default and only accepted value for *`version`* is `v1`. See the docs for examples of using the JSON output: https://docs.brew.sh/Querying-Brew
  - `--installed`: Print JSON of formulae that are currently installed.
  - `--all`: Print JSON of all available formulae.
  - `-v`, `--verbose`: Show more verbose analytics data for *`formula`*.

**e.g : ** 

```bash
antonio@Antonios:~$ brew info zsh
zsh: stable 5.8 (bottled), HEAD
UNIX shell (command interpreter)
https://www.zsh.org/
/usr/local/Cellar/zsh/5.8 (1,531 files, 13.7MB) *
  Poured from bottle on 2020-10-09 at 18:24:00
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/zsh.rb
==> Dependencies
Required: ncurses ✔, pcre ✔
==> Options
--HEAD
	Install HEAD version
==> Analytics
install: 32,464 (30 days), 100,583 (90 days), 486,318 (365 days)
install-on-request: 30,353 (30 days), 94,229 (90 days), 458,122 (365 days)
```



### List all packages installed by Homebrew and their sizes : 

```bash
brew list --formulae | xargs -n1 -P8 -I {} \
    sh -c "brew info {} | grep '[0-9]* files, ' | sed 's/^.*[0-9]* files, \(.*\)).*$/{} \1/'" | \
    sort -h -r -k2 - | column -t
```

**e.g : ** 

```
go                     494.3MB
gcc                    338.7MB
openjdk                319.1MB
gradle                 249.3MB
librsvg                137.6MB
pandoc                 136.1MB
openblas               120MB
hugo                   78.8MB
icu4c                  71.2MB
python@3.8             67.3MB
perl                   63.5MB
node                   62.0MB
pandoc-citeproc        61.8MB
r                      58.8MB
ant                    41.8MB
ruby                   35.3MB
vim                    33.2MB
pipenv                 25.3MB
neovim                 20.4MB
gettext                19.0MB
openssl@1.1            18MB
glib                   15MB
zsh                    13.7MB
gobject-introspection  12.7MB
maven                  10.7MB
bash                   9.5MB
ncurses                8.6MB
harfbuzz               6.2MB
pcre2                  6.0MB
cairo                  5.7MB
pcre                   5.5MB
msgpack                5.2MB
mpfr                   5.1MB
isl                    4.7MB
libunistring           4.4MB
wget                   4.0MB
sqlite                 4MB
libtiff                3.7MB
fontconfig             3.4MB
gdk-pixbuf             3.3MB
gmp                    3.2MB
libuv                  3MB
autoconf               3.0MB
pango                  2.9MB
freetype               2.3MB
luajit                 1.9MB
libevent               1.9MB
readline               1.5MB
pixman                 1.3MB
libpng                 1.2MB
xz                     1.1MB
tmux                   845.4KB
jpeg                   775.2KB
libidn2                727.8KB
utf8proc               650.2KB
gdbm                   641KB
pkg-config             623.7KB
fribidi                609KB
lzo                    546.7KB
libffi                 489.4KB
libmpc                 382.9KB
libyaml                323.5KB
lua                    286.5KB
unibilium              258.3KB
graphite2              235.5KB
libvterm               195KB
tree                   121.1KB
libtermkey             109.3KB
jenv                   72.1KB

```



### taps

- **path** : /usr/local/Homebrew/Library/Taps 

#### Thursday, 8 October, 2020

- **Metadata** :

```bash
Last login: Wed Oct  7 14:42:58 on ttys000
antonio@Antonios-MacBook-Air:~$ brew tap
edgedb/tap
homebrew/cask
homebrew/cask-fonts
homebrew/cask-versions
homebrew/core
antonio@Antonios-MacBook-Air:~$ brew untap edgedb/tap
Untapping edgedb/tap...
Untapped 2 formulae (130 files, 125KB).
antonio@Antonios-MacBook-Air:~$ brew tap
homebrew/cask
homebrew/cask-fonts
homebrew/cask-versions
homebrew/core
antonio@Antonios-MacBook-Air:~$ brew tap AdoptOpenJDK
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/cask).
==> Updated Casks
fsnotes

Error: Invalid tap name 'AdoptOpenJDK'
antonio@Antonios-MacBook-Air:~$ /
-bash: /: Is a directory
antonio@Antonios-MacBook-Air:~$ homebrew-openjdk
-bash: homebrew-openjdk: command not found
antonio@Antonios-MacBook-Air:~$  Watch 
-bash: Watch: command not found
antonio@Antonios-MacBook-Air:~$ brew tap AdoptOpenJDK/homebrew-openjdk
==> Tapping adoptopenjdk/openjdk
Cloning into '/usr/local/Homebrew/Library/Taps/adoptopenjdk/homebrew-openjdk'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 1742 (delta 0), reused 0 (delta 0), pack-reused 1739
Receiving objects: 100% (1742/1742), 321.80 KiB | 663.00 KiB/s, done.
Resolving deltas: 100% (1228/1228), done.
Tapped 43 casks (78 files, 475.9KB).
antonio@Antonios-MacBook-Air:~$ 

```



### leaves

There's an [external command](https://github.com/mxcl/homebrew/wiki/External-Commands) called `brew leaves` which prints all packages that are **not dependencies of other packages**.
`brew leaves` shows all **top-level packages**. That is packages that are not dependencies. This should be the most interesting if you are using the list to re-install packages