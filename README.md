# pi-prompt-stash-ext

Press **F2** to move the prompt you are composing out of the editor so you can
run a slash command. Press **F2** again afterwards to put the draft back and
submit it.

F2 is not a built-in Pi binding and is not bound in tmux's root key table. It
also avoids modifier-encoding differences between terminals.

- Registers F2, unbound by default.
- Toggles per session: stash the draft, then restore it.
- When restoring, anything typed in the meantime is appended after the draft
  instead of being overwritten.
- Warns when there is nothing to stash.
- Stashes are kept per session in process memory, on `globalThis`, so they
  survive `/reload` but not a restart of Pi.

## Install

Install the package from GitHub:

```sh
pi install git:github.com/bhenriq/pi-prompt-stash-ext
```

Then run `/reload` in Pi (or restart it).

Keep it up to date with:

```sh
pi update git:github.com/bhenriq/pi-prompt-stash-ext
# or update every installed package
pi update --extensions
```

Remove it with:

```sh
pi remove git:github.com/bhenriq/pi-prompt-stash-ext
```

### Local development

Run Pi against this checkout for one session:

```sh
pi -e /path/to/pi-prompt-stash-ext
```

Or symlink the checkout into Pi's extension directory, naming the symlink as
you want the extension to appear in Pi:

```sh
ln -s /path/to/pi-prompt-stash-ext ~/.pi/agent/extensions/prompt-stash
```

Then run `/reload` in Pi (or restart it). Do not keep the symlink and the
package install active at the same time, or Pi loads the extension twice.
