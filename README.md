# Dwarf Fortress for Docker

Dwarf Fortress is a game by Bay 12 Games http://bay12games.com/dwarves/

If you enjoy the game, please donate to the patreon.
http://www.patreon.com/bay12games

## How to run

### VNC
Run the container
```
# docker-compose up vnc
```

Connect to the VNC server via port 5901 using your VNC viewer of choice.
Note: macOS has a built-in VNC viewer called Screen Sharing.

The connection password is `password`.

### X11
First, set your display variable (bash)
```
# export DISPLAY=$(ifconfig en0 | grep "inet " | awk '{print $2}'):1
```

Fish version of the above command
```
# set -g -x DISPLAY (ifconfig en0 | grep "inet " | awk '{print $2}'):1
```

Use `socat` to create a socket.
```
# socat TCP-LISTEN:6001,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"
```

Run the container
```
# docker-compose up x11
```
