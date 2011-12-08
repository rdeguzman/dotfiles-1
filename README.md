YADR: Yet Another Dotfile Repo
====

Warning: These dotfiles are opinionated! 

This is a collection of best of breed tools from across the web,
from scouring other people's dotfile repos, blogs, and projects.

In some ways, this is an alternative to janus (https://github.com/carlhuda/janus), offering
many of the same plugins, with minor differnces. But it's also much more,
providing shell customizations (zsh), an irb replacement (pry) with customizations,
and osx settings that are developer friendly (such as fast key repeat),
and remapping your caps-lock to be Esc for vim.

The strongly held opinions expressed here:
---
  * This configuration is for OSX, MacVim, zsh, and pry instead of irb. 
  * Apple-style philosophy: not a lot of choices, but everything Just Works and Looks Good. 
  * All common commands should be two and three character mnemonic aliases - less keystrokes, RSI reduction
  * Most used vim commands should be under your fingertips (home row, prefer Shift to other command keys)
  * Avoid stressful hand motions, e.g. remap Esc to caps lock key, remap underscore to Alt-k in vim
  * Easy to use plugin architecture, no config files to edit.
  * Pick one tool and use it everywhere: vim-ize everything
  * Colors are _important_ - solarized (http://ethanschoonover.com/solarized) is a great looking scheme that is scientifically designed to be awesome.

Differences from janus:
---

  * Much larger and (imho) better curated list of vim plugins
  * Optimized for one color scheme (solarized) means everything Just Looks Good
  * Easy plugin management system using yadr command - no editing of config files
  * No need to replace your vimrc, instead uses overridable submodules (Coming Soon)
  * More than just vim plugins - get great shell aliases, osx, and irb/pry tweaks as well

Before you start
---

 * Remap caps-lock to escape: http://stackoverflow.com/questions/127591/using-caps-lock-as-esc-in-mac-os-x

 * Switch to zsh using oh-my-zh (https://github.com/robbyrussell/oh-my-zsh) in one easy step: 

        wget --no-check-certificate https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh

Submodules
---

This project uses git submodules for some of its plugins. Please run:

    git submodule init; git submodule update

To get all the current plugins, every time you pull this YADR repo. 

Setup for ZSH
---
I am now using ZSH as my default shell because of its awesome globbing
and autocomplete features (the spelling fixer autocomplete is worth the money alone). 

This setup assumes you use oh-my-zsh (https://github.com/robbyrussell/oh-my-zsh)

Place this as the last line in your ~/.zshrc created by oh-my-zsh:

    source ~/.dotfiles/zsh/zshrc

Lots of things I do every day are done with two or three character 
mnemonic aliases. Please feel free to edit them:

    ae # alias edit
    ar # alias reload

Here are some of the customizations you get with this setup:

 * Vim mode
 * Bash style ctrl-R for reverse history finder
 * Fuzzy matching - if you mistype a directory name, tab completoin will fix it

Setup for Pry
---
Pry (http://pry.github.com/) offers a much better out of the box IRB experience 
with colors, tab completion, and lots of other tricks. You should:

    gem install pry
    gem install awesome_print
    ln -s ~/.dotfiles/irb/pryrc ~/.pryrc
    ln -s ~/.dotfiles/irb/aprc ~/.aprc

Use pry

  * as irb: 'pry'
  * as rails console: script/console --irb=pry

Pry customizations:

 * 'clear' command to clear screen
 * 'sql' command to execute something (within a rails console)
 * all objects displayed in readable format (colorized, sorted hash keys) - via awesome_print
 * a few color modifications to make it more useable
 * type 'help' to see all the commands

Setup for Vim
---
To use the vim files:

    ln -s ~/.dotfiles/vimrc ~/.vimrc
    ln -s ~/.dotfiles/vim ~/.vim
    
The .vimrc is well commented and broken up by settings. I encourage you
to take a look and learn some of my handy aliases, or comment them out
if you don't like them, or make your own.

Some of the vim customizations include:
TODO: these customizations will be extracted into a separate keybinding plugin so as not to interfere with standard keybindings 

 * F - instantly Find definition of class (must have exuberant ctags installed)
 * B - show Buffer explorer
 * S - Show buffers in LustyJuggler (use asdfjkl home row keys to then select buffer)
 * T - Tag list (list of methods in a class)
 * K - git grep for the Kurrent word under the cursor
 * O - Open a GitGrep command line with a quote pretyped (close the quote yourself)
 * \mm - show my Marks (set a mark with mX where X is a letter, navigate to mark using 'X). Uppercase marks to mark files, lowercase marks to use within a file.
 * Z - jump back and forth between last two buffers
 * Q - Quit a window (normally Ctrl-w,c)
 * \Q - Kill a buffer completely (normally :bw)
 * Ctrl-j and Ctrl-k to move up and down roughly by functions
 * vv and ss - vertical and horizontal split windows by double tapping
 * H,L,I,M - to move left, right, up, down between windows
 * Ctrl-\ - Show NerdTree (project finder) and expose current file
 * cf - Copy Filename of current file into system (not vi) paste buffer 
 * // - clear the search
 * ,, or z,, - use EasyMotion - type that and then type one of the highlighted letters.
 * Apple-k and Apple-K to type underscores and dashes, since they are so common in code but so far away from home row
 * yw - remapped to yaw, meaning yanking a word will yank the entire word no matter where your cursor is
 * W - write a file (instead of :w, saving you keystrokes for the most common vim operation)
 * gcc (comment a line) via tComment, and gcp custom alias to comment a paragraph
 * Cc - (Current command) copies the command under your cursor and executes it in vim. Great for testing single line changes to vimrc.
 * \ss to run specs, \ll to run a given spec on a line - using my vim-ruby-conque plugin (https://github.com/skwp/vim-ruby-conque)

Included vim plugins
---

 Navigation

 * NERDTree - everyone's favorite tree browser
 * NERDTree-tabs - makes NERDTree play nice with MacVim tabs so that it's on every tab
 * ShowMarks - creates a visual gutter to the left of the number column showing you your marks (saved locations). use \mt to toggle it, \mm to place the next available mark, \mh to delete, \ma to clear all. Use standard vim mark navigation ('X) for mark named X.
 * EasyMotion - hit ,, (forward) or z,, (back) and watch the magic happen. just type the letters and jump directly to your target - in the provided vimrc the keys are optimized for home and upper row, no pinkies
 * LustyJuggler/Explorer - hit B, type buf name to match a buffer, or type S and use the home row keys to select a buffer
 * TagList - hit T to see a list of methods in a class (uses ctags)

 Git

 * fugitive - "a git wrapper so awesome, it should be illegal..". Try Gstatus and hit '-' to toggle files. Git 'd' to see a diff. Learn more: http://vimcasts.org/blog/2011/05/the-fugitive-series/
 * GitGrep - much better than the grep provided with fugitive; use :GitGrep or hit K to grep current word

 Colors

 * AnsiEsc - inteprets ansi color codes inside log files. great for looking at Rails logs
 * solarized - a color scheme scientifically calibrated for awesomeness (including skwp mods for ShowMarks)
 * csapprox - helps colors to be represented correctly on terminals (even though we expect to use MacVim)

 Coding

 * tComment - gcc to comment a line, gcp to comment blocks, nuff said
 * sparkup - div.foo#bar - hit ctrl-e, expands into <code><div class='foo' id#bar/></code>, and that's just the beginning
 * rails.vim - syntax highlighting, gf (goto file) enhancements, and lots more. should be required for any rails dev
 * necomplcache - automatic completion showing, and added Command-Space to select a completion (same as Ctrl-N)

 Utils

 * greplace - use :Gsearch to find across many files, replace inside the changes, then :Greplace to do a replace across all matches
 * ConqueTerm - embedded fully colorful shell inside your vim
 * vim-ruby-conque - helpers to run ruby,rspec,rake within ConqueTerm - use \rr (ruby), \ss (rspec), \ll (rspec line), \RR (rake)
 * vim-markdown-preview - :Mm to view your README.md as html
 * ruby-debug-ide - not quite working for me, but maybe it will for you. supposedly a graphical debugger you can step through

 General enhancements that don't add new commands

 * IndexedSearch - when you do searches will show you "Match 2 of 4" in the status line, nothing new to learn
 * delimitMate - automatically closes quotes 
 * syntastic - automatic syntax checking when you save the file
 * repeat - adds '.' (repeat command) support for complex commands like surround.vim. i.e. if you perform a surround and hit '.', it will Just Work (vim by default will only repeat the last piece of the complex command)


Adding your own vim plugins
---

YADR comes with a dead simple plugin manager that just uses git submodules, without any fancy config files.

    yav -u https://github.com/airblade/vim-rooter

You can update all the plugins easily:

    yuv 

Delete a plugin (Coming Soon)

   ydv -p airblade-vim-rooter

The aliases (yav=yadr vim-add-plugin) and (yuv=yadr vim-update-all-plugins) live in the aliases file.
You can then commit the change. It's good to have your own fork of this project to do that.

Setup for Git
---
To use the gitconfig (some of the git bash aliases rely on my git aliases)

    ln -s ~/.dotfiles/gitconfig ~/.gitconfig

Some of the customizations provided include:

  * git l - a much more usable git log
  * git b - a list of branches with summary of last commit
  * git r - a list of remotes with info
  * git t - a list of tags with info
  * git nb - a (n)ew (b)ranch - like checkout -b
  * git cp - cherry-pick -x (showing what was cherrypicked)
  * git changelog - a nice format for creating changelogs
  * Some sensible default configs, such as improving merge messages, push only pushes the current branch, removing status hints, and using mnemonic prefixes in diff: (i)ndex, (w)ork tree, (c)ommit and (o)bject 
  * Slightly imrpoved colors for diff
  * git unstage (remove from index) and git uncommit (revert to the time prior to the last commit - dangerous if already pushed) aliases

OSX Hacks
---
The osx file is a bash script that sets up sensible defaults for devs and power users
under osx. Read through it before running it. To use:

    ./osx

These hacks are Lion-centric. May not work for other OS'es. My favorite mods include:

  * Ultra fast key repeat rate (now you can scroll super quick using j/k)
  * No disk image verification (downloaded files open quicker) 
  * Display the ~/Library folder in finder (hidden in Lion)

Other recommended OSX tools 
---
 * NValt - Notational Velocity alternative fork - http://brettterpstra.com/project/nvalt/ - syncs with SimpleNote
 * Vimium for Chrome - vim style browsing. The 'f' to type the two char alias of any link is worth it.
 * QuickCursor - gives you Apple-Shift-E to edit any OSX text field in vim.

Credits
---
I can't take credit for all of this. The vim files are a combination of
work by tpope, scrooloose, and many hours of scouring blogs, vimscripts,
and other places for the cream of the crop of vim and bash awesomeness.

COMING SOON
---
 * Full migration to tpope's pathogen format (~/.vim/bundle) for all plugins
 * Better isolation of customizations in smaller chunks, maybe as plugins
 * Automatic setup script to symlink all dotfiles, or just some selectively 


Bash Users
---
I used bash all my life. Last month I switched to zsh. It's nearly 100% backwards compatible
and I promise you, you won't miss bash at all once you derive insane time saving from all the
autocorrect and completion zsh can do for you on the command line.

For more tips and tricks
---
Follow my blog: http://yanpritzker.com
