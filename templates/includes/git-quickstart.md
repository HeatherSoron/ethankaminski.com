# Foreword
Someone (possibly me) has asked you to use Git, and you've never used it before. Maybe you're joining a hardcode coder in a game jam. This guide will show you the very basics, so that you can send your collaborator the code that they're asking for.

This guide is written for terminal usage, but all of the concepts should transfer to a GUI client.

## Installing
If you're using a terminal, the official Git client is probably the way to go on Linux and OS X. On Windows, "Git for Windows" or "git-bash" are probably worth using. This guide _will_ show you all the key terminal commands.

If you need a GUI on Windows or OS X, SourceTree is fairly popular.

# Sync, do stuff, Commit, Push

## Clone - first time sync
In the directory above where you want to create the repository, run `git clone $url`. For example, to clone [my "ludumdare31" repo](https://github.com/ethankaminski/ludumdare-31) into `~/dev/ludumdare31`, run the following:

	# go to the "dev" directory inside our home directory
	cd ~/dev
	git clone https://github.com/ethankaminski/ludumdare-31.git

## Do stuff
Write code, add images, etc., just as you normally would.

## Commit
When you're ready to commit, first *stage* any new or modified files, and then *commit* those files. Use `git add $path` to stage a file or directory, `git commit` to commit all currently-staged files, and `git commit $path` to commit all modified (but _not_ new) files under that path.

For example, commit all new or modified files, from the top-level directory of the repo:

	# remember that '.' is current directory
	git add .
	# no path is needed for git commit, because we've staged the changes already
	git commit

And, to commit all _changed_ files in the `assets/` directory, along with the `copyright.txt` file:

	git commit assets/ copyright.txt

### Commit messages
When you use `git commit`, Git should present you with some sort of text editor (possibly a cli editor, possibly your normal editor). The first line is used as a summary, and a fuller description of your changes goes on subsequent lines. The summary line is required, the description is optional.

A good commit message looks something like the following:

	Added info about commits to the guide

	This adds info about how to commit, including how to write a commit message, and detect files that should be ignored.
	I haven't yet described when to add a description vs. when to omit it. That's more appropriate for a non-quickstart guide.

### Spurious files
Sometimes, when running `git add`, you'll see files that shouldn't be committed. `.DS_Store` on Mac, temporary files created by your IDE, build artifacts, etc..

Before finalizing the commit, check the list of files that are going to be included (you can use `git status`, among other methods).

To deal with those spurious files, ask your resident Git expert to unstage the files, and then help you to add them to an ignore list.

## Pushing
To send your code to the remote repository, use `git push $remoteName $branchName`. In the simplest form, this will be `git push origin master`.

If your push is rejected, it may be because someone else pushed changes that you don't have. This means that a merge will occur, and Git does not allow merges to occur during a push. In this case, you need to do a pull first, resolve the merge locally (it may be automatically resolved for you), and then try pushing again.

## Pulling - subsequent sync
To update your local code, run `git pull $remoteName $branchName`. Again, in its simplest form, this is `git pull origin master`.

If you want to get a little fancier, you can also use `git fetch` followed by `git merge`. This is useful if you want to check what changes have been made, before you pull them.

# Merging
Merging, simply put, is what happens when two people are working in parallel on a project, rather than working one-at-a-time. Merging is incredibly useful, and most of the time, it happens seamlessly. However, because we don't have super-AI yet, sometimes the computer needs assistance during a merge. In particular, Git will sometimes tell you that there is a "merge conflict", which is your cue to help the computer.

If an automatic merge occurs, it's good form to make sure that nothing broke before pushing. Usually nothing breaks, but it's possible that there was an interaction that Git didn't notice (e.g., person A adding a new callsite for the `fooBar()` function, person B renaming the `fooBar()` function).

If a scary message about merge conflicts pops up, make sure that you're *paying attention*, and that you *understand how to resolve the conflict*. I'll write a second guide about this eventually, because merge conflicts are the ONE part of Git which is both risky and common.
