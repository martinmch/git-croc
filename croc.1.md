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

the options are as follows:

**--verbose**
:   Print the output of all hooks to stdout.

**--help**
:   Shows the usage message.

**--test**
:   Run the tests for all hooks in a given stage.

# EXAMPLE

To enable pre-commit hooks, run the following commands:

**$ ln -s croc pre-commit**\
**$ mkdir pre-commit.d**

Add (or symlink) any hooks into this directory to have them run during
pre-commit.

## REGISTERING HOOKS

To register a hook add a link to the hook in the stage.d directory.

## TESTING

To write a test for a hook, create a corresponding folder called
hook.tests. Depending on the hook, put your test files in here. If the
test is supposed to fail, postfix it with ".fails".

# EXIT STATUS

The **hook** utility exists 0 on success, and >0 if an error occurs.

For scripts in the hook directory: Any exit code different from zero
will result in a test failure, otherwise the test will pass.

