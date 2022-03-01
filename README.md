# kzenv

[![GitHub Actions Status](https://github.com/nlamirault/kzenv/workflows/main/badge.svg?branch=master)](https://github.com/nlamirault/kzenv/actions)

[Kustomize](https://www.kustomize.io/) version manager mainly inspired by [tfenv](https://github.com/tfutils/tfenv)

## Support

Currently kzenv supports the following OSes

- [x] Linux (64bit)
- [ ] Mac OS X (64bit)

## Installation

### Automatic

For Archlinux users :

```console
$ wget https://github.com/nlamirault/kzenv/releases/download/v1.0.0/kzenv-1.0.0-1-x86_64.pkg.tar.zst
$ sudo pacman -U kzenv-1.0.0-1-x86_64.pkg.tar.zst
```

For OSX users :

Installing the tap will provide access to software via Homebrew:

```console
$ brew tap nlamirault/kzenv https://github.com/nlamirault/kzenv/
```

Installing individual software tools can then be done as follows:

```console
$ brew install kzenv
```

### Manual

On any other platform, you can install kzenv as follows:

1. Check out kzenv into any path (here is `${HOME}/.kzenv`)

  ```console
  $ git clone https://github.com/nlamirault/kzenv.git ${HOME}/.kzenv
  ```

2. Add `${HOME}/.kzenv/bin` to your `$PATH` any way you like

  For Bash
  ```console
  $ echo 'export PATH="${HOME}/.kzenv/bin:$PATH"' >> ${HOME}/.bash_profile
  ```

  For Zsh :
  ```console
  echo 'export PATH="${HOME}/.kzenv/bin:$PATH"' >> ${HOME}/.zprofile
  
  or
  
  echo 'export PATH="${HOME}/.kzenv/bin:$PATH"' >> ${HOME}/.zshrc
  ```

  OR you can make symlinks for `kzenv/bin/*` scripts into a path that is already added to your `$PATH` (e.g. `/usr/local/bin`) `OSX/Linux Only!`

  ```console
  $ ln -s ${HOME}/.kzenv/bin/* /usr/local/bin
  ```

  You can create `${HOME}/bin` or `${HOME}/.local/bin` and on next login it will get added to the session `$PATH`
  or by running `. ${HOME}/.profile` it will get added to the current shell session's `$PATH`.

  ```console
  $ mkdir -p ~/.local/bin/
  $ . ~/.profile
  $ ln -s ~/.kzenv/bin/* ~/.local/bin
  $ command -v kzenv
  ```

## Github API

`kzenv` use Github API to check releases. You could set the `GITHUB_API_TOKEN`
environment variable to use the authenticated API

## Usage

### kzenv install [version]

Install a specific version of Kustomize. Available options for version:

- `i.j.k` exact version to install

```console
$ kzenv install 0.7.0
```

### kzenv use [version]

Switch a version to use

```console
$ kzenv use 3.4.0
```

### kzenv uninstall [version]

Uninstall a specific version of Kustomize

```console
$ kzenv uninstall 3.3.0
```

### kzenv list

List installed versions

```console
$ kzenv list
* 3.4.0 (set by /home/nicolas/Projects/kzenv/version)
  3.3.0
  2.0.3
```

### kzenv list-remote

List installable versions

```console
% kzenv list-remote
3.4.0
3.4.0
3.3.0
3.3.0
3.2.3
3.2.3
...
3.0.0
3.0.0
2.1.0
2.1.0
2.0.3
2.0.3
2.0.2
2.0.2
2.0.1
2.0.1
2.0.0
2.0.0
1.0.11
...
1.0.6
1.0.6
...
```


#### .kustomize-version

If you use a [.kustomize-version file](#kustomize-version-file), `kzenv install` (no argument) will install the version written in it.


## Upgrading

```console
$ git --git-dir=~/.kzenv/.git pull
```

## Uninstalling

```console
$ rm -rf /some/path/to/kzenv
```

## LICENSE

- [kzenv itself](https://github.com/nlamirault/kzenv/blob/master/LICENSE)
- [tfenv](https://github.com/tfutils/tfenv/blob/master/LICENSE)
  - kzenv partially uses tfenv's source code
