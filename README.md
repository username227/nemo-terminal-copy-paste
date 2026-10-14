# nemo-terminal-copy-paste
Changes nemo-terminal copy and paste shortcuts from ctrl-shift-c and ctrl-shift-v to ctrl-c to ctrl-v without affecting regular copy and paste functions in nemo

## Deconflicting the shortcut
The standard terminal command used by ctrl-c is to send a SIGINT to stop the command and return to a prompt. By installing this shortcut, you will create a conflict with this shortcut key. In order to deconflict this shortcut, you will want to consider changing your default shortcut by editing .bashrc with something like:
```
if [[ -o interactive && -e /dev/tty ]]; then
    stty intr '^X' </dev/tty 2>/dev/null
fi.
```
This will change the shortcut to ctrl-X. Note that if you do this in .bashrc will do this for all terminals, not just nemo-terminal.
