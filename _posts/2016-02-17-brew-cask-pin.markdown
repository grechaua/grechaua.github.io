---
layout: post
title:  "Brew cask install old version and pin it"
date:   2016-02-17 01:22:00 +0200
categories: brew
---
Because of some tricky chef provision procedure I have to revert my vagrant version.

At first I removed current version of vagrant by: 
`brew cask uninstall vagrant`

After that I changed my `vagrant.rb` in `/usr/local/Library/Taps/caskroom/homebrew-cask/Casks`
with specific `version` and `sha256` sum.

And install this specific version via:
```brew cask install vagrant```

Now my provision works, but if I run 
```brew update && brew upgrade``` my vagrant version will be the latest again

Common method to pin package doesn't work:
```brew pin Caskroom/cask/vagrant```

I've compared with native brew pinned formula, i.e. `ansible` and observed there was symlink in dir:
```ls -l /usr/local/Library/PinnedKegs``` like:
```ansible -> ../../Cellar/ansible/1.7.2```

So to pin cask package I've created symlink manually:
```cd /usr/local/Library/PinnedKegs && ln -s /opt/homebrew-cask/Caskroom/vagrant/1.7.4 vagrant```

As result I have the old specific version of cask formula and it still works due brew update and upgrade.