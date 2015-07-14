**pathed** is a small utility which edits and queries the paths stored in the Windows registry that are used to search for executables. There are two of these path settings:
```
HK_CURRENT_USER\Environment\PATH
```
and:
```
HK_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment\PATH
```
By default, **pathed** works on the first, which is the per user path applied after the system path. Changes to this should be as Douglas Adams said "mostly harmless". However:

**_PATHED CAN SCREW UP YOUR SYSTEM! IT CHANGES THE REGISTRY! IF YOU DON'T KNOW WHAT YOU ARE DOING WITH IT, DON'T USE IT!_**

Also, note that **pathed** changes the registry - not the path of your current shell. To pick up the registry changes you will need to start a new shell.

Having got that out of the way, here are the **pathed** operating modes:
```
pathed 
```
prints out a help screen
```
pathed -l
```
lists the user PATH as currently stored in the registry. If you want to list the system path, use **pathed -l -s**.
```
pathed -e
```
lists the PATH as currently set in the PATH environment variable. Note the -s flag is not applicable to this command.
```
pathed -g file
```
searches (greps) all the directories on the path for "file" and prints out all occurrences - a bit like the Linux "type" facility.
```
pathed -q some-dir
```
checks is some-dir is on the user path, returning 0 (i.e.success) to the calling environment if it is, and non-zero if it isn't. This is intended to be used in scripts. If you want to query the system path, use **pathed -q -s**.
```
pathed -v
```
verifies that all directories on the path actually exist. As with all commands, by default it only checks the user path. Use -s to check the system path.
```
pathed -p
```
checks that path entries exist and are not duplicates (in the same registry key). It prunes entries that fail this test and writes a new path to the registry. As usual, use -s to prune the system path.
```
pathed -a some-dir
```
Add some-dir to user path. You guessed it, to add to the system path, use -s as well. pathed checks if directories exist and won't add them if they do not - to defeat this behaviour, use the -f flag.
```
pathed -r some-dir
```
Remove some-dir from user path, or from system path if -s specified.

For most of the commands, variables like %systemroot% in paths are not expanded - specifically they are not expanded for the -a and -r commands. If you want them expanded, use the -x flag.

Since version 0.6, you can use long option names. The long names are:
```
--add
--remove
--query
--grep
--list
--prune
--verify
--system
--force
--expand
--env
```
when these were added I also tightened up the parameter parsing - you can no longer say (for example):
```
pathed -a -s somedir
```
you must say:
```
pathed -a somedir -s
```