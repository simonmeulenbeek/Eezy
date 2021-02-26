# eezy

Eezy is a super simple project automation system for ***all*** your projects.

Eezy makes it easy to create and run simple tasks.

## Quickstart

```shell
project-folder>eezy init
Initializing current directory as an Eezy folder.
Finished initializing. Start adding tasks by using 'eezy add-task new-task'.
Or use 'eezy help' for more information.
project-folder>eezy add-task new-task
Task 'new-task' created.
project-folder>eezy edit new-task
project-folder>eezy new-task
Eezy - Running task 'new-task'
Eezy - finished running task 'new-task' in 0 second(s).
```


## How does it work?

Tasks in Eezy are just simple bash scripts. Eezy is in actuality just a simple management and execution wrapper for creating and running these scripts. 

The fact that tasks in Eezy are simple bash scripts makes them: 
* Powerful - Automate anything with a CLI
* Easy to understand - It's just BASH with some extras
* Easy to edit - Use your favorite editor!
* Easy to manage with VCS

By using certain conventions we can extend the power and usefulness of these simple scripts. For example, by sourcing the task-scripts into eezy itself, variables become available to the tasks itself. 

Adding to that, Eezy allows you to add global variable scripts, that are available to all tasks. A good application for these would be urls or secrets, or any other task-spanning data.


## Getting started
Eezy and Eezy tasks are only available in Eezy enabled folders. 

You can enable Eezy in a folder by using the `init` command:

```shell
my-folder> eezy init
```

Now you can start creating tasks by using the `add-task` command:
```shell
my-folder> eezy add-task a-new-task
Created new task 'a-new-task'
```

You can run your task by using eezy with your task-name:
```shell
my-folder> eezy a-new-task
Eezy - Running task 'a-new-task'
Eezy - Finished running task 'a-new-task' in 1 second(s).
```

