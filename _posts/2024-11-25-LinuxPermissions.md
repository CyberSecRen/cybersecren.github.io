---
layout: post
title:  "Managing File Permissions with Linux"
summary: "Using Linux Command Line to Manage File Permissions"
author: Renato Ferreira
date: '2024-11-25 14:35:23 +0530'
category: Access_Control
thumbnail: /assets/img/posts/LinuxThumbnail.png
keywords: Linux, permissions, access controls
permalink: /blog/linuxpermissions/
usemathjax: true
---

# Managing File permissions in Linux
<br><br>

## Project description
<br>

Using Linux commands to check and edit permissions on files and directories within a network.
<br><br>

##### Check file and directory details
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Using `ls -l` will show permissions for any non-hidden files in the directory as well as subdirectories within the working directory. Using `ls -la` will show all permissions for hidden and non-hidden files in the directory as well as the permissions for any subdirectory within the working directory. In this directory, when using `ls -l`, the permissions are as follows for file project_k.txt: -rw-rw-rw. This means that all groups have read and write permissions for this file.
<br><br>

##### Describe the permissions string
<br>

&nbsp;&nbsp;&nbsp;&nbsp;A permission string for a file will start with a `-` while a permission string for a directory will start with `d`. A typical permission string for a file or directory could look like this(the first character is different depending on whether it is a directory or a file): drwdrwdrwd. The d at the beginning shows that the permission is for a directory. Each set of 3 letters after represents the permissions for user, group and other in that order. User is for the owner of the file, group is for the group the file belongs to and other is anyone else who is able to find the file that is not in the group or the user. The r is for read permissions which allow that set of permissions to read the file. The w is for write permissions which allows the user to edit the subdirectory or file. The x is for execute permissions which allows the user to access the subdirectory or the file’s contents. If a permission group does not have the permission, the letter is replaced by a hyphen as seen in the example above.
<br><br>

##### Change file permissions
<br>

&nbsp;&nbsp;&nbsp;&nbsp;For project_k.txt, you would need to change the “other” permissions to remove the write permission. This could be done in two ways. You could remove the write permission specifically by using `chmod o-w project_k.txt` or you could also use `chmod o=r project_k.txt` which would change the write and execute permissions if necessary as well as maintaining the read permission.
<br><br>

##### Change file permissions on a hidden file
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Since the file .project_x.txt is a hidden file (indicated by the fact it begins with a “.”), it is necessary to use the `ls -la` command in order to see the permissions for hidden files. To change the permission, the easiest command to use would be `chmod u=r,g=r .project_x.txt` in order to change the user and group permissions to read only. The command `chmod u-w,g-w+r .project_x.txt` could also be used but it is slightly longer.
<br><br>

##### Change directory permissions
<br>

&nbsp;&nbsp;&nbsp;&nbsp;Using `ls -l` will show the subdirectory “drafts” inside of the working directory. The permissions are as follows: drwx--x---. This means that the user and the group both have permissions to execute which would allow group members to access the drafts directory. In order to remove these permissions, the command `chmod g-x drafts` would be used in order to remove the executable permissions from the group.
<br><br>

##### Summary
<br>

&nbsp;&nbsp;&nbsp;&nbsp;In summary, this is how permission management is done within Linux Bash. Using these commands, the security of directories and files within them are highly improved and can be used throughout the network in order to minimize surface area in the case of an attack and prevent accidental or intentional changes to the files and directories by employees who should not have permissions.
<br><br>