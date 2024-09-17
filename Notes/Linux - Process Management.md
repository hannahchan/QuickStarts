# Linux - Process Management

Linux systems can run multiple processes. The following is a quick guide on how to manage them from the command line.

## View running processes

Display Linux processes with repetitive updates using;

    $ top

Alternatively you can use `htop` if installed which is a more interactive version of `top`.

To view a snapshot of the current processes, use;

    $ ps

By default `ps` doesn't show much information. To get a more complete picture of the processes running on the system, try;

    $ ps -aux

Remember that you can pipe the output of `ps` to `grep`. For example;

    $ ps -aux | grep bash

To quickly find the Process IDs (PIDs) of a process you know the name of, you can use `pgrep`. For example;

    $ pgrep bash

## Send process signals

All processes in Linux respond to signals. Signals are the operating system's way of telling programs to terminate or modify their behavior.

Signals are often sent using the `kill` command. For example;

    $ kill <PID> ...

When no signal is specified, the default signal sent is `TERM`. This is equivalent to;

    $ kill -TERM <PID> ...

To force the terminal of a process, you can use the `KILL` signal.

    $ kill -KILL <PID> ...

To see all the possible signals you can send with the `kill` command, run;

    $ kill -l

If you only know the process name, you can send signals using the `pkill` or `killall` command.

## Adjust process priorities

To share and manage CPU resources, processes are assigned a priority `PR` and niceness `NI` value in Linux. The assigned values are viewable for each process in the `PR` and `NI` columns when you run the `top` command.

**Priority** - The priority value is the actual priority that is used by the Linux kernel to schedule a task. Values are 0 to 139 in which 0 to 99 is used for real-time processes and 100 to 139 is used for user-space processes.

**Niceness** - Niceness values are user-space values that can be used to control the priority of a process. Values are -20 to +19 where -20 is the highest, 0 the default and +19 is the lowest.

The niceness values map to the *user-space* priority values 0 to 39. The relationship between the two can be expressed as;

    PR = NI + 20

To launch a process with a certain niceness value, you can use the `nice` command.

    $ nice -n <ADJUSTMENT> <COMMAND> <ARGS> ...

To alter the niceness value of an already process, you can use `renice`.

    $ renice -n <PRIORITY> <PID>

## Manage foreground and background processes

By default, processes started in a terminal run in the foreground. This means that until the running process exits or changes state, you will be blocked from interacting with the shell.

To stop a foreground process from blocking access to the shell, you can send it the `SIGINT` signal to terminate the process it in most cases by pressing;

    CTRL + C

Alternatively you can suspend the process by sending the `SIGTSTP` signal by pressing;

    CTRL + Z

To view your suspended processes, you can use the command;

    $ jobs

To resume running the process in the foreground, you can use the command;

    $ fg %1

Where `%1` is the reference to the job number.

To resume running the process in the background, you can use;

    $ bg %1

Use the `kill` command to terminate a background process.

To send process to the background while stating it, simply append `&` to the end of your command. For example;

    $ ping www.google.com &

Foreground and background processes are tied to the terminal that started them. When a terminal closes, it typically sends a `SIGHUP` signal to all of its processes to terminate. If you know in advance that you would like your process to keep running even when the terminal closes, you can use the `nohup` command to start your process. If you have already started your process, you can use the `disown` command.

## References

1. What is Process Management in Linux?

    - <https://www.scaler.com/topics/process-management-in-linux>

2. How To Use ps, kill, and nice to Manage Processes in Linux

    - <https://www.digitalocean.com/community/tutorials/how-to-use-ps-kill-and-nice-to-manage-processes-in-linux>

3. How To Use Bash's Job Control to Manage Foreground and Background Processes

    - <https://www.digitalocean.com/community/tutorials/how-to-use-bash-s-job-control-to-manage-foreground-and-background-processes>

4. A brief guide to priority and nice values in the linux ecosystem

    - <https://medium.com/@chetaniam/a-brief-guide-to-priority-and-nice-values-in-the-linux-ecosystem-fb39e49815e0>