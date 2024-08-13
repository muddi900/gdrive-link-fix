# Transform Google Drive Bulk Links to a single column
When you copy multiple links from google drive, they are comma-space(`, `) separated.

I wanted pasted them in a doc so I use sed. I had to do it multiple times, so I turned it into a script.

Of course, it can replace `, ` with a new line in any text

## Installation

Requires git

```sh
git clone https://github.com/muddi900/gdrive-link-fix && cd gdrive-link-fix
```

## Usage

### macOS

Once you have copied links in bulk from Google Drive you can use the built-in `pbpaste` command to pipe it to the script.

```sh
pbpaste | sed -f gdrive-link-fix.sed
```

You can pipe the output back to clipboard using the built in `pbcopy` command.

```sh
pbpaste | sed -f gdrive-link-fix.sed | pbcopy
```

### Linux

Most Linux distros do not come with something akin to `pbcopy` and `pbpaste`. On X based systems you can use `xclip` or `xsel` utils.

You may have to install them using your preferred package manager.

```sh
xclip -selection clipboard -o | sed -f gdrive-link-fix.sed
```

```sh
xsel --clipboard --output | sed -f gdrive-link-fix.sed
```

You can also paste the links in a file and edit in place.

```
sed -i -f gdrive-link-fix.sed /path/to/gdrive-link-list.txt
```

### Add to PATH

You can use the script from anywhere without using the whole path if you add the script directory to path.

Open your shell config file (`~/.bashrc` or `~/.zshrc` usually) in your preferred text editor(*Emacs*, or *vim* if you're a degenerate)  and add this line:

```sh
PATH="$PATH:/path/to/gdrive-link-fix/"
```

## Contributions

There isn't much to add to this, but if you have something in mind, feel free to open an issue.
