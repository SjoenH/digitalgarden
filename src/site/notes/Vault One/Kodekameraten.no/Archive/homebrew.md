---
{"dg-publish":true,"permalink":"/vault-one/kodekameraten-no/archive/homebrew/"}
---

# ---
# title: Homebrew
# author: Henry S. Sjøen
# date: 2019-03-21 15:28:31 +0000
# description: Homebrew is an amazing tool for Mac OS that is invaluable for any developer.
# tags: howto,getting started,english
# draft: true
# dg-publish: true
# ---
Homebrew is an amazing tool for Mac OS that is invaluable for any developer.

> It installs the stuff you need that Apple didn’t.

Homebrew simplifies installing developer tools, but you may also install other applications without having to search online, download an installer, follow some GUI-steps, then remembering to trash the installer-junk... You get the point.

* [Installing stuff](#installing-stuff)
* [Installing "normal" stuff](#installing-%22normal%22-stuff)
* [Install Homebrew](#install-homebrew)
* [Formula vs Casks](#formula-vs-casks)

## Install Homebrew

Paste this line into your MacOS Terminal prompt

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

## Installing stuff

Homebrew makes unix-tools easily accessible.
If you are wondering if some software is available you can search for it.

Let's look for [Wget](https://www.gnu.org/software/wget/).

```bash
➜  ~ brew search wget
==> Formulae
wget                                                                wgetpaste
➜  ~
```

We got a hit! If we would we could install it with `brew install`, but it's good practice to check what running a _formulae_ would actually do. Let's run `brew info`.

```bash
➜  ~ brew info wget
wget: stable 1.20.1 (bottled), HEAD
Internet file retriever
https://www.gnu.org/software/wget/
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/wget.rb
==> Dependencies
Build: pkg-config ✔
Required: libidn2 ✔, openssl ✘
==> Options
--HEAD
	Install HEAD version
==> Analytics
install: 160,363 (30 days), 494,408 (90 days), 1,428,639 (365 days)
install_on_request: 140,903 (30 days), 426,829 (90 days), 1,244,784 (365 days)
build_error: 0 (30 days)
➜  ~
```

Let's go ahead and install it with `brew install`.

```bash
brew install wget
```

And that should be it! Wget should now be installed on your computer.

## Installing "normal" stuff

As well as installing gnu/unix-tools (like wget) we may also install _normal_ applications with homebrew.

In Homebrew, installing something like [Ableton Live](https://ableton.com) looks like this:

```bash
brew cask install ableton-live
```

And upgrading it is as easy as: `brew cask upgrade ableton-live`

Or you can upgrade all casks by running `brew cask upgrade`

## Formulaes vs Casks

Homebrew is usually used to install CLI-tools/programs ( aka. stuff you use in your terminal).

They are available as **_formulaes_** It looks like this. `brew install <app>`

**_Casks_** are for installing GUI-applications and making maintaining stuff easier.
`brew cask` installs macOS apps, fonts and plugins and other non-open source software.
`brew cask upgrade` ugprades an app.