# Why?

## Why this guide?
I'm working with two Git newbies for [Ludum Dare](http://ludumdare.com/compo/) 34, and I've previously spent time explaining Git. 

### Command-line vs. graphical interface
I use the command-line interface for Git. Therefore, most of the examples will use the command-line syntax. 

## Why source control?
We've all been there: you've made a change that broke something, and you don't remember how to undo it. Or, a collaborator has given you a patch, but it's on an out-of-date version of a file that you've been working on, and now you have to combine the changes.

Source control helps to solve those problems, and a number of others. You don't _have_ to use source control, but it makes coding much easier to manage - especially once it gets past one person working as a hobby.

# Basic Usage
The basic workflow in Git is simple. You pull the upstream code (to make sure you're up-to-date), make changes, commit once you have something worth saving, and then push when you're done. You may also need to merge, which is usually simple. For the cases where it isn't, see the "Merging" section (seriously, it has some important advice about merging!).

## Installation
If you're comfortable with a terminal, then using the command line version of Git will make it easier to follow along with this guide. On Windows, "git-bash" is a passable way to run Git via command line.

If you're not comfortable with a terminal, then [SourceTree](https://www.sourcetreeapp.com/) is a popular Windows/Mac GUI client. It provides a "Terminal" button for those cases where the UI doesn't have a button for what you need to do, and it seems to match up fairly well to how the cli version works (although I remember some inconsistency with the words "reset" and "revert").

## Repository set-up
The first thing you need to do is create a local repository for the project that you're working with.

### Existing repo
Navigate to the directory _above_ where the top-level repository directory will be, and run:
	git clone ${existingUrl} [$targetDirectory]
If you omit the "$targetDirectory" argument, it will automatically choose a directory name based on the 

### New repo
Navigate to the top-level directory of your project, and run `git init`. Later on, you may need to run `git remote add origin $url` to tell it what the "origin".

## Syncing up with others


## When to commit?
Each project will have its own standards, but to use my own general guideline, you want to commit when you think you'll want to come back to the current state of progress, or when you're worried about losing your progress.

You've completed a feature? Great, that should definitely be a commit. You've made something less buggy than it was before, and you're worried that the rest of the bugfixing could make things worse? For a Git beginner, I advise you to also commit that.

# Merging (this is important!)
Now, merging. Merging is one of the most powerful parts of Git, and also one of the most dangerous - _if_ you're not being careful.

# Ignoring files (build artifacts, etc.)
Sometimes, you don't want to add a file to Git. For example, build artifacts should usually not be tracked in Git, because they change frequently, and can be derived from the other files in the project.
In those cases, you can use a file named `.gitignore`, in any directory of the project. Inside the gitignore file, list the files or directories that you don't want to track. The paths are relative to the directory containing that gitignore file.

For example, a project using Node.js and Python, with a file that provides per-developer configuration, might have the following gitignore file in the top-level directory of the project:

	# ignore files tracked by a dependency manager (like npm)
	node_modules
	# ignore compiled Python files
	*.pyc
	# ignore our local configuration file, so that we don't clobber other people's local config
	config/local.json


