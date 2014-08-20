% CROC(1) croc 1.0.0
% Martin Christiansen
% August 2014

# Name
croc - run tests in various git stages

# SYNOPSIS

Not to be called directly.

# DESCRIPTION

The croc script is symlinked to the name of a git hook stage. See
**githooks(5)** for git hook stages and when they are triggered.

When a git hook is triggered, each script in the corresponding directory will
get executed.

Each script must be an executable ordinary file, with a name less than
71 characters. To disable a script, append ".skip" to the filename.

To enable these git hooks, configure your git hook dir to be the
directory of these files.

**$ git config core.hooksPath ".hooks"**

# EXAMPLE

To enable pre-commit hooks, run the following commands:

**$ ln -s croc pre-commit**\
**$ mkdir pre-commit.d**

Add (or symlink) any hooks into this directory to have them run during
pre-commit.

# EXIT STATUS

The **hook** utility exists 0 on success, and >0 if an error occurs.

For scripts in the hook directory: Any exit code different from zero
will result in a test failure, otherwise the test will pass.

