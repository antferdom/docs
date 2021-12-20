# tmux 

[TOC]



## metadata

**Prefix** : The default prefix key is `C-b`, which means the `Ctrl` key and `b`

***NOTE*** :  changes added to the file **.tmux.conf**

```
 1 unbind C-b
 2 set -g prefix `
```

**Prefix'** : The default prefix key is ` ` `

- **.tmux.conf** (dotfile)

```bash
  1 unbind C-b
  2 set -g prefix `
  3 bind-key ` last-window
  4 bind-key e send-prefix
  5 
  6 
  7 set -g status-position bottom
  8 set -g status-bg colour234
  9 set -g status-fg colour137
 10 set -g status-left ''
 11 set -g status-right '#[fg=colour233,bg=colour241,bold] %d/%m #[fg=colour233,bg=colour245,bold] %H:%M:%S '
 12 set -g status-right-length 50
 13 set -g status-left-length 20
 14 set -g mouse on
 15 
 16 setw -g window-status-current-format ' #I#[fg=colour250]:#[fg=colour255]#W#[fg=colour50]#F '
 17 setw -g window-status-format ' #I#[fg=colour237]:#[fg=colour250]#W#[fg=colour244]#F '
```



## core commands


- **Access help** : 

**Schema** : 

​															**`?**

**e.g** : 

```bash
~$ `?
```

- **Split window vertically in two panes** : 

**Schema** : 

​															**`"**

**e.g** : 

```bash
~$ `"
```

- **Switching among panes of the same window (Changing the active pane)** : 

**Description** : The active pane can be changed between the panes in a window with these key bindings:

- C-b Up, C-b Down, C-b Left and C-b Right change to the pane above, below, left or right of the active pane. These keys wrap around the window, so pressing C-b Down on a pane at the bottom will change to a pane at the top.
- **C-b q** prints the pane numbers and their sizes on top of the panes for a short time. Pressing one of the number keys before they disappear changes the active pane to the chosen pane, so C-b q 1 will change to pane number 1.
- C-b o moves to the next pane by pane number and C-b C-o swaps that pane with the active pane, so they exchange positions and sizes in the window.

These use the `select-pane` and `display-panes` commands.

Pane numbers are not fixed, instead panes are numbered by their position in the window, so if the pane with number 0 is swapped with the pane with number 1, the numbers are swapped as well as the panes themselves.

**Schema** : 

​															**`q**

**e.g** : 

```bash
~$ `q
```

- **Listing sessions** : 

**Description** : The list-session command (alias ls) shows a list of available sessions that can be attached

**Schema** : 

​															**tmux ls** 

**e.g** : This shows four sessions called 1, 2, myothersession and mysession:

```bash
$ tmux ls
1: 3 windows (created Sat Feb 22 11:44:51 2020)
2: 1 windows (created Sat Feb 22 11:44:51 2020)
myothersession: 2 windows (created Sat Feb 22 11:44:51 2020)
mysession: 1 windows (created Sat Feb 22 11:44:51 2020)
```



## Issues

- **Scroll up** :

**Description** : There is a limit in the buffer that limits the maximun content beging displayed on the prompt.

**Fix** : 

