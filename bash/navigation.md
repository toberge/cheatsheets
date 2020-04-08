# Navigation

## Where am I now?

Depending on your shell prompt, you should see some form of path or folder name to the left of where you type your commands.

Regardless of that, you can print your current location with `pwd`.

Your current folder will hereafter be referred to as "where you stand"

## Getting around

Use `cd` to change your current directory.  
You can specify both absolute and relative paths.

```bash
cd /usr/share/applications
```

If you stand in a folder and wanna get down to some subfolder, you do not need to supply the entire path:

```bash
cd some/subfolder/below
```

The folder `.` is always your current folder, whereas `..` is the folder above, the parent directory.

```bash
cd . # does nothing
cd .. # moves you up *one* directory
cd ../.. # moves you up *two* directiories
```

## Location stack

It is possible to push and pop locations on a history stack using the `pushd` and `popd` builtins.

```bash
# starting in /home/yourname
pushd /etc/conf.d
popd
# guess what, now we are back in our home directory
pushd ../someothername
# and now we're peeping in on another user
pushd /usr/share/applications
# two directories on the stack
popd
popd
# this leaves us back in ~ again
```

Se `pushd --help` and `popd --help` for some options.

