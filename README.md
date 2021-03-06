# task
 A CLI reminders and task management toolkit, Written by Will Russell/Scotchman0
 
Last patch update: 7/3/22

version 1.0.1

# About
Task offers a CLI interface for managing personal or shared tasks/reminders that have the ability to alert at a scheduled time + self remove entries.

# RECENT PATCH:
Major Overhaul

The first major revision of TASK now supports the following:
- A unified and multi-user interface task queue
- Configuration selections available with 'task config' to set common variables
- Organized column layout for easier viewing and management
- Utilizes 'at' and 'atq' for job tasking + alerts, also inits a self-cleanup of reminder at ETA when alert fires (this can be ignored by not setting an ETA (value 0)
- Default install directory is at ~/task-path/ but for group use, would advise installing it in /opt (set the variable and run task with sudo once to place all the files), then grant group ownership + read/write on the files to allow others to update tasks. (then move the task script to a common executable location like /usr/local/bin

# NEXT UPDATE GOALS:
- Toggle option for 'delete task on complete y/n' --> create a secondary ATQ entry for removing task, defaults to 'N'
- increase options for setting ETA instead of just in hours (currently supports whole hour increments up to 24)

# Overview:
A simple CLI task manager that lets you print strings to a file for CLI recall/management. Echos contents to `~/.*shrc` on new shell startup and can be called manually with 'task'

The main branch is explicitly for shared task management on compute endpoints. This was purpose-built to support alerting users what jobs are running 
The simplified branch will be used for single-user project tasking and 'todo' handling (less group-oriented)

# Usage:
~~~
#######  task help #######

command usage: $ task <option> <string>



 -h|help: print this brief help

 -n|--new: create new reminder entry --> $ task -n 'buy eggs'

 >>> '-n' has follow-up prompts: ETA for reminders and a GPU in-use Y/N prompt

 -d|--delete: delete line entry by number... ex: 'task -d 3'

 -C|--clear: purge all reminders from list

 config: open an editor and modify the config file to set options

 edit: opens an editor to modify the raw task file to modify entries manually



description of task columns:



   JOB       |     TASK      |  ETA   |       ATQ         |  GPU  | USER

<job number> | <description> | <time> | <reminder number> | <Y/N> | <username>



JOB      TASK                                          ETA     ATQ    GPU   USER

1   This is an example task                            20:59   +64+   Y     will

2   Docker training in progress                        NONE   +NONE+   N    john

#######  task help #######
~~~
