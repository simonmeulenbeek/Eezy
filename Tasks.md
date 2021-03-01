# Eezy Tasks

### About
This document describes Eezy Tasks. By design Eezy is supposed to prevent requiring the user to learn something new, so this document should always be very short. 

Since version 1.2, Eezy will pass parameters to Tasks. This changes how Tasks work, and so prompts the creation of this document. This document will keep track of all the significant differences between Eezy Tasks and regular bashfiles.

### changelog

* v1.2 - Creation of this document


## Definition of an Eezy Task
An Eezy Task is a bashfile in an `.eezy` folder. 

Eezy Tasks are basically the same as bashfiles except for the following differences:

* There is no need for the 'shebang' at the start of the file (i.e. no `#!/bin/bash`)
* Eezy Tasks have access to variables exposed by Eezy
* Eezy Tasks can't have the same name as any of the built-in Eezy commands: `help`, `version`, `init`, `list`, `add-task` or `edit` .

### Variables
The current list of exposed variables are:

| var | contains | example|
|---|---| --- |
|EEZY_VERSION | Current Eezy version | `v1.2` |
|PROJECT_FOLDER | Path to the directory where eezy was run from | `/home/user/projects` |
|EEZY_FOLDER | Path to the directory that contains the Eezy Tasks| `/home/user/projects\.eezy` |
|TASK_PATH | Path to the current running task | `/home/user/projects\.eezy\task` |
|TASK_NAME | Name of current running task | `task` |

#### Parameters
Parameters in Eezy work the same as in bash (`$1`, `$2`, `$3`, etc.), except for the fact that Eezy 'consumes' the first parameter (the name of the task). See the example below:
```shell
~ $ eezy test-parameters 1 2 3 4 5 6 7 8
$0=./eezy
$1=1
$2=2
$3=3
...
```
If you need to reference the name of the task, you can ofcourse use `$TASK_NAME`