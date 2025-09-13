# Process Management in Linux

## Introduction to process management
A **process** is an instance of a running program. Linux provides multiple utilities to monitor, manage, and control processes effectively.  
Each process has a unique **Process ID (PID)** and belongs to a **parent process**.

##  Index of Commands covered
###  Viewing Processes
- `ps aux` – View all running processes  
- `ps -u username` – View processes for a specific user  
- `ps -C processname` – Show a process by name  
- `pgrep processname` – Find a process by name and return its PID  
- `pidof processname` – Find the PID of a running program  

###  Managing Processes
- `kill PID` – Terminate a process by PID  
- `pkill processname` – Terminate a process by name  
- `kill -9 PID` – Force kill a process  
- `pkill -9 processname` – Kill all instances of a process  
- `kill -STOP PID` – Stop a running process  
- `kill -CONT PID` – Resume a stopped process  
- `renice -n 10 -p PID` – Lower priority of a process  
- `renice -n -5 -p PID` – Increase priority of a process (requires root)  

### Background & Foreground Processes
- `command &` – Run a command in the background  
- `jobs` – List background jobs  
- `fg %jobnumber` – Bring a job to the foreground  
- `Ctrl + Z` – Suspend a running process  
- `bg %jobnumber` – Resume a suspended process in the background  

### Monitoring System Processes
- `top` – Interactive process viewer  
- `htop` – User-friendly process viewer (requires installation)  
- `nice -n 10 command` – Run a command with a specific priority  
- `renice -n -5 -p PID` – Change priority of an existing process  

### Daemon Process Management
- `systemctl list-units --type=service` – List all system daemons  
- `systemctl start service-name` – Start a daemon/service  
- `systemctl stop service-name` – Stop a daemon/service  
- `systemctl enable service-name` – Enable a service at startup  


##  Viewing Process Details

### Using **ps**
 Show processes for a specific user:  
  
  ps -u username

 Show a process by name:

  ps -C processname

### Using **pgrep**

 Find a process by name and return its PID:

  pgrep processname

### Using **pidof**

 Find the PID of a running program:

  pidof processname


## Managing Processes

### Killing Processes

 Terminate by PID:

  kill PID

Terminate by process name:

  pkill processname

 Force kill a process:

  kill -9 PID
 
 Kill all instances of a process:

  pkill -9 processname

### Stopping & Resuming Processes

 Stop a running process:
 
  kill -STOP PID

 Resume a stopped process:

  kill -CONT PID

### Changing Process Priority

View process priorities:

  top  # Look at the NI column

Change priority of a running process:

  renice -n 10 -p PID  # Lower priority (positive values)
  
  renice -n -5 -p PID  # Higher priority (negative values, root required)


##  Running Processes in the Background

 Run a command in the background:

  command &
 
 List background jobs:

  jobs

Bring a job to the foreground:

  fg %jobnumber
  
 Send a running process to the background:

  Ctrl + Z  # Suspend process
  
  bg %jobnumber  # Resume in background
 

##  Monitoring System Processes

### Using **top**

Interactive process viewer:

* Press `k` and enter a PID to kill a process.
* Press `r` to renice a process.
* Press `q` to quit.

### Using **htop**

A user-friendly alternative to top:

htop

 Allows mouse-based interaction for process management.

### Using **nice** & **renice**

 Run a command with a specific priority:

  nice -n 10 command
 
 Change the priority of an existing process:

  renice -n -5 -p PID


##  Daemon Processes

 List all system daemons:

  systemctl list-units --type=service

 Start a daemon:

  systemctl start service-name

 Stop a daemon:

  systemctl stop service-name
  
 Enable a service at startup:

  systemctl enable service-name
 



