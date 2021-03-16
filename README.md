# Eezy
Eezy is a super simple project automation system for ***all*** your projects. 

```shell
~ $ eezy init
~ $ eezy add-task new-task
~ $ eezy edit new-task
~ $ eezy new-task
Eezy - Running task 'new-task'
Eezy - finished running task 'new-task' in 0 second(s).
```

When developing software I often find myself repeating the same commands everytime I want to run, test or deploy something. Creating scriptfiles is often my solution, but I tend to forget about these when returning to work on older projects. Eezy eliminates this problem by standardizing the way of creating and running these scripts ('tasks'). Eezy stores tasks in a standardized location, so it's super easy to either commit or .gitignore your tasks. 

### Changelog

* 1.3 - Editor argument, removal of `eval`, improved install task on MacOS
* 1.2 - Tasks Parameters, add [Tasks.md](Tasks.md)
* 1.1 - Add Install Script
* 1.0 - Initial release

### Table of Contents
- [Eezy](#eezy)
    - [Changelog](#changelog)
    - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Installation](#installation)
  - [Usage](#usage)
    - [CLI Options](#cli-options)
  - [Technical details](#technical-details)
    - [Eezy](#eezy-1)
    - [Tasks](#tasks)
  - [Contributing](#contributing)

## Introduction
Tasks in Eezy are just shell scripts. Eezy is in actuality just a simple management and execution wrapper for the creation and running of these scripts. 

The fact that tasks in Eezy are simple bash scripts makes them: 
* Powerful - Automate anything with a CLI
* Easy to understand - It's just BASH with some extras
* Easy to edit - Use your favorite editor!
* Easy to manage with VCS

By using certain conventions we can extend the power and usefulness of these simple scripts. For example, by sourcing the task-scripts into Eezy itself, variables become available to the tasks itself.

## Installation
Since v1.1 Eezy comes with a handy install task included in the release. 

```shell
~ $ wget https://github.com/simonmeulenbeek/Eezy/releases/download/v1.3/eezy.zip
~ $ unzip eezy.zip
~ $ ./eezy install
```

To install Eezy manually, download and unpackage the latest Eezy release, and move `eezy` to a directory that's included in PATH, e.g. `~/.local/bin` .

```shell
~ $ wget https://github.com/simonmeulenbeek/Eezy/releases/download/v1.3/eezy.zip
~ $ unzip eezy.zip
~ $ cp eezy ~/.local/bin
```

## Usage
Eezy is a command line application. To start adding and running tasks you need to first navigate to your directory and enable Eezy. You can enable Eezy in your current directory by using `eezy init` . You can add tasks with `eezy add-task taskname` . You can run tasks with `eezy taskname` . Look below for an example and a full list of available commands. 

**example**
```shell
~/project-folder $ eezy init
Initializing current directory as an Eezy folder.
Finished initializing. Start adding tasks by using 'eezy add-task new-task'.
Or use 'eezy help' for more information.
~/project-folder $ eezy add-task new-task
Task 'new-task' created.
~/project-folder $ eezy edit new-task
~/project-folder $ eezy new-task
Eezy - Running task 'new-task'
Eezy - finished running task 'new-task' in 0 second(s).
```

### CLI Options
Eezy comes with 6 built in commands.
* `eezy help` - List available built-in commands.
* `eezy version` - Shows Eezy version
* `eezy init` - Intialize Eezy in the current directory.
* `eezy list` - List available tasks.
* `eezy add-task [taskname]` - Create a new Eezy task for this directory. 
* `eezy edit [taskname] [editor]` - Edit an existing Eezy task. The `[editor]` argument is optional. If no editor is given, it will use `$VISUAL`, `$EDITOR` or `nano` (in that order).
  
After adding tasks you can run them by simply invoking eezy followed by a taskname. 

`eezy [taskname]`


## Technical details

### Eezy
Tasks are bash-files that live in the `.eezy` folder of a specific directory. When running a task with Eezy, Eezy looks for the task in the `.eezy` directory in the current folder. Note that this means that Eezy tasks are only available to that specific folder. 

Enabling Eezy in a directory means the creation of an `.eezy` folder. Eezy makes this easy with `eezy init`
```shell
~/project-folder $ eezy init
Initializing current directory as an Eezy folder.
Finished initializing. Start adding tasks by using 'eezy add-task new-task'.
Or use 'eezy help' for more information.
```

To create a new task you can either use `eezy add-task` or manually create a new file in the `.eezy` folder. The filename will be the name of the new task.
```shell
~/project-folder $ eezy add-task a-new-task
Created new task 'a-new-task'
```

To edit your task either use `eezy edit` or edit the file in the `.eezy` folder using a texteditor.
```shell
~/project-folder $ eezy edit a-new-task
```
**NB**: `eezy edit` uses the prefered editor set by `$VISUAL` or `$EDITOR`. It falls back on nano if those aren't set. Since version 1.3 you can also provide a preferred editor as an argument. If you need to provide some argument to your editor you need to enclose it within double-quotes.
```shell
~/project-folder $ eezy edit a-new-task code
~/project-folder $ eezy edit a-new-task "code --argument-for-code --open-file"
```

### Tasks

Moved, see [Tasks](Tasks.md)


## Contributing
Please create a new Issue if you find any bug or problem while using Eezy. Also create an issue if you have any (feature-)suggestions. 

Eezy is very accepting to forking and pull requests. Pull requests will be accepted if they fix bugs or increase usefulness, and don't include any dependencies.

