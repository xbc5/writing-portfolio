# Work Smarter, Not Harder: 10x Your Terminal Productivity With These 5 Tools

## Fzf: Lightning-Fast Searches in a Fuzzy Bottle

This is not a standalone tool but a utility that you can use with other tools. Essentially it's an interactive search and filter tool: It accepts a list of items and displays it—you then interactively type to narrow the result.

It uses a fuzzy search algorithm, which simply means "close approximation search"; for example, `li x` would match `Linux`."

### Why Fzf Makes Forgotten Filenames a Non-Issue

Why is that useful? Because when you're in the flow, typing in the terminal, going from command to command, directory to directory, the last thing you want to be is specific.

Perhaps you're searching for something but cannot remember the exact name; perhaps there's a pattern within a file, but you cannot remember if it's uppercase, lowercase, or even the exact phrase.

A close approximation (fuzzy) search will match the closest value, always.

### 60-Second Installation to Change Your Terminal Workflow Forever

It's a simple tool, so it's best just to dive in.

Choose an installation command:

```sh
apk add fzf
apt-get install fzf
brew install fzf
dnf install fzf
pacman -S fzf
```

Then run this command to see what it does:

```sh
cd ~
ls | fzf
```

Now type something and watch how it updates the list in real-time. When you hit return, it will "echo" that name. This means that it fits nicely in a shell script, or you can pipe (send) the results into another command. For example:

```sh
cat `ls -f | fzf`
```

This command allows you to pick any file (in the current directory) and read its contents.

### Fzf in the Wild: Some Real-World Examples to Get You Started

There are lots of use cases for fzf, and it's one of my favorite tools when writing shell scripts. It's a convenient way to prompt the user to select something from a large list of items.

For example, pick a process to kill:

```sh
ps aux | fzf | awk '{print $2}' | xargs kill -9
```

Check environment variables:

```sh
env | fzf
```

Fzf is a staple for most who use the terminal, employing it in hundreds of different ways across hundreds of different applications. Neovim plugins, for example, use it to find files by their name, contents, and more.

The number of applications is broad and unbounded, so specifying them all here is not possible.

## Zoxide: Stop Typing Full Paths Like a N00b

[Zoxide](https://github.com/ajeetdsouza/zoxide) is a small and simple utility that records all of the directories that you visit and allows you to fuzzy search over those directories and "jump" to them. It's quick, painless, and it forgives typos.

It integrates (in one form or another) with over 20 popular applications, including Yazi, Emacs, and Neovim.

### Get Zoxide Running on Any System (No Fuss)

There are packages for most platforms—"extra" repositories, core repositories, and multi-platform repositories, like [Cargo](https://crates.io/crates/zoxide), [Conda](https://anaconda.org/conda-forge/zoxide), [Guix](https://packages.guix.gnu.org/packages/zoxide/), etc. It's easy to install, and it's just as easy to configure and use.

The installation processes vary, so it's best to refer to the documentation.

### First-Time Zoxide Setup: Paste This And Go

Once installed, you need to set up your environment before you can use it. Put the following command into your shell configuration file:

```sh
eval "$(zoxide init bash)"
```

This command spits out its configuration code that your shell will evaluate every time it loads. Reload your shell—choose one of:

```sh
source ~/.bashrc
source ~/.zshrc
```

### `z` Is All You Need

After you've initialized your shell environment, you need to build up a history of visited directories before zoxide becomes useful:

```sh
cd ~/Downloads
cd /
z Down
```

`Down` is a close approximation of "Downloads," so `z Down` should change you to `~/Downloads`. When there's more than one match, it prompts you to choose one with fzf.

## Yazi: Why The Shell Is Not Enough

The shell is great, and tools like zoxide make it a breeze to move around, but these tools do not provide the same visibility that file managers do, e.g., file and directory previews.

Navigating with a file manager allows you to peek inside of directories, files, and images with little to no effort. Couple that with the ability to exit back to the shell at the current working directory: The right file manager bridges the visibility gap. You can switch between the file manager and shell seamlessly, leverage convenient navigation commands, and drop into the shell to run manual commands.

[Yazi](https://yazi-rs.github.io/) is one such command-line file manager, and it's my favorite.

### Async Means That It Doesn't Freeze

Yazi is a modern take on [Ranger](https://github.com/ranger/ranger) that promises to be faster. [Ranger blocks the UI while it works](https://github.com/sxyazi/yazi/discussions/806#discussioncomment-9178860); Yazi does not.

Yazi is asynchronous, which simply means that you can continue using the application while it performs tasks in the background.

### You Can Share State Between Instances

In addition to the task queue, it has a messaging system that allows you to communicate anything between instances, typically to share state, configuration, or to synchronize commands.

### Yazi + Zoxide: Breaking The Speed Limit

It has built-in support for zoxide, so you can fly around the file system at the speed of light.

### Plugin Power: How to Extend Yazi Beyond Its Limits

```sh
ya pack -a owner/repo
```

You can also create custom plugins to fit your needs.

Once you have an established workflow, you often find yourself repeating the same actions over and over. These actions are perfect for automation.

If you don't know how to write Lua, this is the perfect project to learn. However, be careful that you do not accidentally delete any important files.

### Vim Keys Meet File Management: _BLAZING_ Fast Navigation 🔥

Yazi's best feature is that it mirrors Vim controls closely: movement and modifications—h, j, k, l; yank/paste; delete—are all familiar.

Yazi also has commands that allow you to copy file paths, file names, file names without extensions, the current working directory, and more. Once you commit these to memory, it's more convenient than working in the command shell.

### Install It Anywhere

If you use Debian, you will need to compile it yourself. For Fedora, Arch, and other distributions, there are community packages available. There is also a Snap and Flatpak available, so there's an installation path for everyone.

## Zellij: Because Tmux is a Full-Time Job

Zellij is a terminal multiplexer, which means that you can create multiple _virtual_ terminals within your terminal and lay them out as you wish. It's a modern take on Tmux.

Tmux extensions are often difficult and time-consuming to configure, and they frequently go unmaintained. With Zellij, you get some core, powerful features for free, with zero configuration.

Zellij also uses Vim controls, and it displays contextual keymap information in a status bar. This makes it both familiar (to Vim users) and easy to pick up.

### Search Your Scrollback Like a Vim Pro

One of the features that I find myself using a lot is the search functionality: you can move into search mode with `Ctrl+s, s`. Like Vim, you can skip through the highlighted results with `n` and `p`.

Search has other features like case sensitivity, whole words, and page scrolling. I use it a lot to find specific outputs from commands.

### Own Your Scrollback Buffer: Discard the Noise and Keep What's Important

Another feature that complements search is the ability to edit the scrollback buffer. This means that you can open the entire terminal scrollback in your editor. Use `Ctrl+s, e`, and Zellij will open it in your `$EDITOR` (your system's default).

I use this to go through log files using a powerful text editor like Neovim: I delete what I don't need, then save the output somewhere for further analysis. This opens up a world of powerful plugins via your text editor or even its command shell. I use this often to process JSON with jq and lean heavily on Neovim's powerful editing capabilities.

### Why Session Recovery Makes Reboots Painless

The core reason that I use terminal multiplexers is to restore previous sessions. A session is the state of your terminals upon save: the applications that you have open and their layouts.

I work in virtual machines non-stop, so I'm always stopping and starting systems. My layouts and open windows disappear every time. It's difficult to set this up multiple times each day.

Zellij automatically saves my session so it can recall it the next time that I boot up the system. After I choose my session, it restores all of the applications and layouts exactly as they were.

### Copy-and-Paste With the Mouse—A Guilty Pleasure

One simple and intuitive feature that Zellij provides is the ability to copy text by simply highlighting it with your mouse. I know that this is not in the spirit of terminal usage, but we've all done it, and the times that we've tried to do it and it didn't work, we wished that it did.

## Atuin: Stop Retyping Commands Already

Atuin is nearly identical to a tool that I use: [zsh-fzf-history-search](https://github.com/joshskidmore/zsh-fzf-history-search). Both provide fuzzy search capabilities over their search history, but Atuin provides some extra features, and the authors have broader goals for it to become more than a search tool.

### Execute Commands 10x Faster

Firstly, fuzzy searching over my command history is the best invention ever for the shell. Have you ever typed out a long command more than once? Without auto-completion? It's difficult, and mistakes are common.

Typically people will just use the up arrow to cycle through their command history, but fuzzy search is a powerful and convenient way to search and filter.

To fuzzy search, you only need to provide a close approximation of your command, and it narrows down the list in real-time to the closest match.

Re-running commands every 10 seconds is now a pleasure. I can run repeat or difficult commands in less than a second: a 10x speedup.

### Sync With Their Server or Your Own—Your Choice

Atuin uses a client-server model: the client (you) and the sync server (to store and share state). State includes configuration, command history, and even shell aliases.

The connection to the server is end-to-end encrypted -- so if you're worried about privacy, then Atuin has you covered.

In addition to that, there are different server options:

- Public server: Atuin provides a free public server;
- Self-hosted: The authors provide the server as a Docker image, so you can host it anywhere that you want, with the protection of E2E encryption; in addition, you can host via K8 or systemd—if you don't know what K8 is, then it doesn't apply to you.

If you're _really_ paranoid about privacy, you can disable sync altogether and just use the powerful fuzzy search feature by itself.

### Looking Forward

I said that Atuin has broader goals to be more: it intends to become a shell environment sync service—dotfiles (configuration files) and shell aliases (custom command names for complex commands).

In fact, you can create and sync shell aliases now, for example:

```sh
atuin dotfiles alias set lsf "ls -f"
```

### Atuin is More Than Just `Ctrl+r`

Atuin enables advanced search criteria: search by working directory, host, or session.

These criteria won't be useful _all_ of the time; however, the need to recall commands executed on a specific host, session, or within a specific (project) directory is not uncommon. When your history becomes large enough and your commands similar enough, these extra filters will become useful.
