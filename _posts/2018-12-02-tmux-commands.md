---
layout: post
title: Some Basic Tmux Commands
description: This post shows some sample usage of the tool tmux by illustrating a typical workflow.
redirect_from:
  - /blog/2018/12/02/some-basic-tmux-commands.html
---

[Tmux][1]{:target="_blank"} is a command-line tool which lets you run and manage multiple programs in one single terminal, and is commonly used on remote machines accessed via SSH.

You may find this tool particularly useful when you need to deal with, and keep an eye on, time-consuming processes that you run on a remote server.

Simply put, tmux allows you to reattach running programs to another terminal after logging off from an SSH session.

In a typical workflow, you create a *tmux session* or attach to an existing one. Within a session, you manage multiple *windows* which are basically virtual terminals where you run programs.

## Tmux Sessions

Create a session.

```
tmux
```

List active sessions.

```
tmux ls
```

Attach to a session.

```
tmux attach -t <target-session>
```

## Windows

| Keyboard Shortcut    | Result                         |
|----------------------|--------------------------------|
| `CTRL`+`b`, then `d` | Detach from current session.   |
|----------------------|--------------------------------|
| `CTRL`+`b`, then `c` | Create a new window.           |
|----------------------|--------------------------------|
| `CTRL`+`b`, then `n` | Switch to the next window.     |
|----------------------|--------------------------------|
| `CTRL`+`b`, then `p` | Switch to the previous window. |

Close a window.

```
exit
```

[1]: https://github.com/tmux/tmux/wiki
