# Happy Prime dotfiles

The structure and many (most?) of the files in this repository are forked
from [Jeremy's dotfiles](github.com/jeremyfelt/dotfiles), which were in turn
forked from [Zach Holman's dotfiles](https://github.com/holman/dotfiles).

### Components

There's a few special files in the hierarchy.

- **bin/**: Anything in `bin/` will get added to your `$PATH` and be made
  available everywhere.
- **Brewfile**: This is a list of applications for [Homebrew](https://brew.sh) to install.
- **topic/\*.zsh**: Any files ending in `.zsh` get loaded into your
  environment.
- **topic/path.zsh**: Any file named `path.zsh` is loaded first and is
  expected to setup `$PATH` or similar.
- **topic/completion.zsh**: Any file named `completion.zsh` is loaded
  last and is expected to setup autocomplete.
- **topic/\*.symlink**: Any files ending in `*.symlink` get symlinked into
  your `$HOME`. This is so you can keep all of those versioned in your dotfiles
  but still keep those autoloaded files in your home directory. These get
  symlinked in when you run `script/bootstrap`.

## Install

Run this:

```sh
git clone https://github.com/happyprime/dotfiles.git ~/dotfiles
cd ~/dotfiles
script/bootstrap
```

This will symlink the appropriate files in `dotfiles` to your home directory.
Everything is configured and tweaked within `~/dotfiles`.

The main file you'll want to change right off the bat is `zsh/zshrc.symlink`,
which sets up a few paths that'll be different on your particular machine.

`dot` is a simple script that installs some dependencies, sets sane OS X
defaults, and so on. Tweak this script, and occasionally run `dot` from
time to time to keep your environment fresh and up-to-date. You can find
this script in `bin/`.

`reload!` is included to re-source new aliases, etc...

## Applications to install manually and other caveats.

### Download and install

* **Code**
    * After installation, open VS Code and use the command palette to install the shell command.
    * Install intelephense: `code --install-extension bmewburn.vscode-intelephense-client`
	* Install WP Hooks: `code --install-extension johnbillion.vscode-wordpress-hooks`
	* Install PHP Debug: `code --install-extension xdebug.php-debug`

### Caveats

* Valet is installed via a Composer script. These commands should be run manually afterward:
    * `valet install`
	* `valet use php@7.4`
	* `brew services start mariadb`
	* Inside a `~/Development` directory, `valet park`.
* **Xcode** - I don't really understand the relationship between Xcode and the terminal, but strange stuff happens and then I find myself installing this.
	* I really thought `xcode-select --install` was supposed to take care of things, but it likely does cd /usrnot. /shrug
