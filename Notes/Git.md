# Git #

Git is a free and open source distributed version control system commonly used by developers. It can be downloaded and install on Linux, MacOS and Windows from https://git-scm.com.

## Learning Git ##

There are heaps of resources on the internet from where you can learn Git. Here are some of them below:

1. Resources to learn Git
    - https://try.github.io

2. Code School: Git Real
    - https://app.pluralsight.com/library/courses/code-school-git-real

3. Code School: Get Real 2
    - https://app.pluralsight.com/library/courses/code-school-git-real-2

## First-Time Git Setup ##

Git uses a user name and email to associate commits with an identity. Before you start making commits, you will want configure Git with your user name and email. For more information about this, please check out;

https://git-scm.com/book/en/Getting-Started-First-Time-Git-Setup

### Setting your Git user name and email for every repository on your computer ###

In your terminal, use the following commands to set your Git user name and email.

    $ git config --global user.name "<Your Name>"
    $ git config --global user.email "<Your Email>"

To confirm that you have set the Git user name and email correctly, type the following.

    $ git config --global user.name
    $ git config --global user.email

### Setting your Git user name and email for a single repository ###

In your terminal, change to the working directory of the local repository and use the following commands to set your Git user name and email.

    $ git config user.name "<Your Name>"
    $ git config user.email "<Your Email>"

To confirm that you have set the Git user name and email correctly, type the following.

    $ git config user.name
    $ git config user.email

## Customizing Git ##

At some point you will want to configure Git further. You can make Git configuration changes to one of three levels.

1. System - Applies to all users on the system
2. Global - Applies only to you
3. Local - Applies to a single repository

Each level overrides values in the previous level.

- Configurations values in Global override System.
- Configurations values in Local override both System and Global.

The `git config` command is used to set configuration values. Simple add the options `--system`, `--global` or `--local` to the command to tell it which level to modify. `--local` is assumed if not specified. Since Git configurations are stored as plain text files, you can also edit them directly to configure Git.

For more information about `git config` and what you can actually configure, please checkout the following;

- https://git-scm.com/book/en/Customizing-Git-Git-Configuration
- https://git-scm.com/docs/git-config

### Check your settings ###

To check your current Git configuration, you can run one of the following commands;

    $ git config --list
    $ git config --list --show-origin
    $ git config --list --system
    $ git config --list --global
    $ git config --list --local

## Git Quick References ##

1. Git - Reference
    - https://git-scm.com/docs

2. Git Quick Reference
    - http://jonas.nitro.dk/git/quick-reference.html

3. git - the simple guide
    - http://rogerdudler.github.io/git-guide/
