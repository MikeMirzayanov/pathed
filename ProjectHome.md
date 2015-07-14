
```
pathed is a command-line tool for changing and querying the path in the registry

Version 0.8
Copyright (C) 2011 Neil Butterworth

usage: pathed [-a dir | -r dir | -e | -l | -q dir | -v | -p | -g file] [-s] [-f] [-x]

pathed -a dir    adds dir to the path in  the registry
pathed -r dir    removes  dir from the path in the registry
pathed -l        lists the entries on the current path in the registry
pathed -e        lists the entries on the current path in the PATH environment variable
pathed -q dir    queries registry, returns 0 if dir is on path, 1 otherwise
pathed -g file   searches (greps) the path for all occurrences of file
pathed -v        verifies that all directories on the path exist
pathed -p        prunes the path by removing duplicates and non-existent directories

By default, pathed works on the path in HKEY_CURRENT_USER. You can make it use
the system path in HKEY_LOCAL_MACHINE by using the -s flag.

Normally pathed will check a directory exists on disk before adding it to the
path. To prevent this, use the -f flag.

Paths containing environment variables such as %systemroot% will not normally have
the variables expanded to their values. To expand them, use the -x flag

AS WITH ALL COMMANDS THAT CHANGE THE REGISTRY, PATHED CAN CAUSE DAMAGE IF YOU
DO NOT KNOW WHAT YOU ARE DOING. IF IN DOUBT, DO NOT USE IT!
```