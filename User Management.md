# User Management in Linux

Introduction to User Management in Linux
Linux is a multi-user operating system, meaning multiple users can operate on a system simultaneously. Proper user management ensures security, controlled access, and system integrity.

## Key files involved in user management:

● /etc/passwd – Stores user account details.

● /etc/shadow – Stores encrypted user passwords.

● /etc/group – Stores group information.

● /etc/gshadow – Stores secure group details.

## Creating Users in Linux

● To create a new user in Linux, use:

useradd username --- This creates a user without a home directory.

adduser username ----This create a user with a home directory:

● To specify a shell:

useradd -s /bin/bash username

### adduser Command (For Debian-based systems)

adduser username

This is an interactive command that asks for a password and additional details.

## Managing User Passwords

● To set or change a user’s password:

passwd username

Enforcing Password Policies

● Password expiration: Set password expiry days

chage -M 90 username

● Lock a user account

passwd -l username

● Unlock a user account

passwd -u username


## Modifying Users

Modify an existing user with usermod:

● Change the username:

usermod -l new_username old_username

● Change the home directory:

usermod -d /new/home/directory -m username

● Change the default shell:

usermod -s /bin/zsh username

## Deleting Users

● To remove a user but keep their home directory:

userdel username

● To remove a user and their home directory:

userdel -r username

## Working with Groups

● Creating Groups

groupadd groupname

● Adding Users to Groups

usermod -aG groupname username

● Viewing Group Memberships

groups username

● Changing Primary Group

usermod -g new_primary_group username

## Sudo Access and Privilege Escalation

##Adding a User to Sudo Group

● On Debian-based systems:

usermod -aG sudo username

● On RHEL-based systems:

usermod -aG wheel username

## Granting Specific Commands with Sudo

● Edit the sudoers file:

visudo

Then add:

username ALL=(ALL) NOPASSWD: /path/to/command










