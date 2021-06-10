# p4u p4 utility (p4u) to fill up the gap of p4 itself.

It is based on bash script thus working with bunch of shell commands.  It works
on top of `p4` binary as released officially but filled the gap for features and
things that could be better.

> For someone coming from `git` to use perforce via its cli 'p4', I bet you know
> what was missing in the latter.

# Installation

You can just clone this repository, then symblink `p4u` file into your executable
path e.g. `/usr/local/bin/`, or you can copy the file there.

To make a symlink from `p4u` to `/usr/local/bin/p4u`, you can execute the following
command

```
ln -s `pwd`/p4u /usr/local/bin/p4u
```

assume that you are currently at the project directory, and you have permission
to create a file at target directory. Otherwise, you might need `sudo`.

# Configuration

Configuration is configured through environment variables for now, until there
would be much more settings to be made, we might change the way to do this.

Set the following environment variables through your aliased or profile file
e.g. `~/.bash_aliases` or `~/.bash_profile`; for example `export
<CFG-NAME>=<CFG-VALUE>`

* `P4U_BIN` - to change which `p4` binary to use inside the script

  It is a high chance that you would be working on WSL 1/2 with perforce. The
  project should be able to built on Windows platform, and able to interact with
  command line on WSL. `p4` binary for WSL won't work as it cannot adapt to use
  the correct path for each platform correctly. So using `p4.exe` which is a
  binary for Windows version, but we execute it on WSL is the solution as it
  understands Windows path correctly. Thus it becomes this setting. Most likely,
  just set `P4U_BIN=p4.exe` should be fine for WSL environment.

# Features

## `p4u describe`

Original `p4 describe` has limitation as follows

* It doesn't show (additional) diff of newly added files on the shelved
  changelist.
* It outputs in non-unified (non-git compatible) format, it needs a particular
  flags to make it output just that
* It outputs excessed header text although it's good, but sometimes we want to
  directly pipe it to ` ... | view -` (`vim`) to see as diff format immediatley
without manual removal of such header lines.

Usages as implemented

* `p4u describe -S=123456`
* `p4u describe -S=123456 --no-header`

# License MIT, Wasin Thonkaew
