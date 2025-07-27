[TOC]

# Sessions
## Start a new session
| Command |
| ------- |
| `$ tmux` |
| `$ tmux new` |
| `$ tmux new-session` |
| `: new` |

## Start a new session with the name `mysession`
| Command |
| ------- |
| `$ tmux new -s mysession` |
| `: new -s mysession` |

## Kill/Delete session `mysession`
| Command |
| ------- |
| `tmux kill-ses -t mysession` |
| `tmux kill-session -t mysession` |

## Kill/Delete all sessions, but the current
| Command |
| ------- |
| `$ tmux kill-session -a` |

## Kill/Delete all sessions, but `mysession`
| Command |
| ------- |
| `$ tmux kill-session -a -t mysession` |

## Rename session
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>$</kbd> |

## Detach from session
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>d</kbd> |

## Detach others on the session
(Maximize window by detach other clients)
| Command |
| ------- |
| `: attach -d` |

## Show all sessions
| Command |
| ------- |
| `$ tmux ls` |
| `$ tmux list sessions` |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>s</kbd> |

## Attach to last session
| Command |
| ------- |
| `$ tmux a` |
| `$ tmux at` |
| `$ tmux attach` |
| `$ tmux attach-session` |

## Attach to a session with the name `mysession`
| Command |
| ------- |
| `$ tmux a -t mysession` |
| `$ tmux at -t mysession` |
| `$ tmux attach -t mysession` |
| `$ tmux attach-session -t mysession` |

## Session and Window Preview
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>w</kbd> |

## Move to previous session
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>(</kbd> |

## Move to next session
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>)</kbd> |

# Windows 
## Start a new session with the name `mysession` and window `mywindow`
| Command |
| ------- |
| `$ tmux new -s mysession -n mywindow` |

## Create window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>c</kbd> |

## Rename current window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>,</kbd> |

## Close current window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>&</kbd> |

## List windows
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>w</kbd> |

## Previous window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>p</kbd> |

## Next window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>n</kbd> |

## Switch/select window by number
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>0</kbd> `...` <kbd>9</kbd> |

## Toggle last active window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>l</kbd> |

## Reorder window, swap window number 2(src) and 1(dst)
| Command |
| ------- |
| `: swap-window -s 2 -t 1` |

## Move current window to the left by one position
| Command |
| ------- |
| `: swap-window -t -1` |

# Panes
## Toggle last active pane
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>;</kbd> |

## Split the current pane with a vertical line to create a horizontal layout
| Command |
| ------- |
| `: split-window -h` |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>%</kbd> |

## Split the current with a horizontal line to create a vertical layout
| Command |
| ------- |
| `: split-window -v` |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>"</kbd> |

## Join two windows as panes (Merge window 2 to window 1 as panes)
| Command |
| ------- |
| `: join-pane -s 2 -t 1` |

## Move pane from one window to another (Move pane 1 from window 2 to pane after 0 of window 1)
| Command |
| ------- |
| `: join-pane -s 2.1 -t 1.0` |

## Move the current pane left
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>{</kbd> |

## Move the current pane right
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>}</kbd> |

## Switch to pane to the direction
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>↑</kbd>|
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>↓</kbd>|
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>→</kbd>|
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>←</kbd>|

## Toggle synchronize-panes(send command to all panes)
| Command |
| ------- |
| `: setw synchronize-panes` |

## Toggle between pane layouts
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>Space</kbd> |

## Switch to next pane
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>o</kbd> |

## Show pane numbers
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>q</kbd> |

## Switch/select pane by number
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>0</kbd> `...` <kbd>9</kbd> |

## Toggle pane zoom
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>z</kbd> |

## Convert pane into a window
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>!</kbd> |

## Resize current pane height(holding second key is optional)
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> <kbd>+</kbd> <kbd>↑</kbd> |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>↑</kbd> |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> <kbd>+</kbd> <kbd>↓</kbd> |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>↓</kbd> |

## Resize current pane width(holding second key is optional)
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> <kbd>+</kbd> <kbd>→</kbd> |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>→</kbd> |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> <kbd>+</kbd> <kbd>←</kbd> |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>←</kbd> |

## Close current pane
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>x</kbd> |

# Copy Mode
## Use vi keys in buffer
| Command |
| ------- |
| `: setw -g mode-keys vi ` |

## Enter copy mode
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>[</kbd> |

## Enter copy mode and scroll one page up
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>PgUp</kbd> |

## Quit mode
| Command |
| ------- |
| <kbd>q</kbd> |

## Go to top line
| Command |
| ------- |
| <kbd>g</kbd> |

## Go to bottom line
| Command |
| ------- |
| <kbd>G</kbd> |

## Scroll up
| Command |
| ------- |
| <kbd>↑</kbd> |

## Scroll down
| Command |
| ------- |
| <kbd>↓</kbd> |

## Move cursor left
| Command |
| ------- |
| <kbd>h</kbd> |

## Move cursor down
| Command |
| ------- |
| <kbd>j</kbd> |

## Move cursor up
| Command |
| ------- |
| <kbd>k</kbd> |

## Move cursor right
| Command |
| ------- |
| <kbd>l</kbd> |

## Move cursor forward one word at a time
| Command |
| ------- |
| <kbd>w</kbd> |

## Move cursor backward one word at a time
| Command |
| ------- |
| <kbd>b</kbd> |

## Search forward
| Command |
| ------- |
| <kbd>/</kbd> |

## Search backward
| Command |
| ------- |
| <kbd>?</kbd> |

## Next keyword occurance
| Command |
| ------- |
| <kbd>n</kbd> |

## Previous keyword occurance
| Command |
| ------- |
| <kbd>N</kbd> |

## Start selection
| Command |
| ------- |
| <kbd>Space</kbd> |

## Clear selection
| Command |
| ------- |
| <kbd>⎋ Esc</kbd> |

## Copy selection
| Command |
| ------- |
| <kbd>⏎ Enter</kbd> |

## Paste contents of buffer_0
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>x</kbd> |

## display buffer_0 contents
| Command |
| ------- |
| `: show-buffer ` |

## copy entire visible contents of pane to a buffer
| Command |
| ------- |
| `: capture-pane ` |

## Show all buffers
| Command |
| ------- |
| `: list-buffers ` |

## Show all buffers and paste selected
| Command |
| ------- |
| `: choose-buffer ` |

## Save buffer contents to buf.txt
| Command |
| ------- |
| `: save-buffer buf.txt ` |

## delete buffer_1
| Command |
| ------- |
| `: delete-buffer -b 1 ` |

# Misc
## Enter command mode
| Command |
| ------- |
| <kbd>^ Ctrl</kbd> <kbd>+</kbd> <kbd>b</kbd> &nbsp;&nbsp; <kbd>x</kbd> |

## Set OPTION for all sessions
| Command |
| ------- |
| `: set -g OPTION` |

## Set OPTION for all windows
| Command |
| ------- |
| `: setw -g OPTION` |

## Enable mouse mode
| Command |
| ------- |
| `: set mouse on` |

# Help
## List key bindings(shortcuts)
| Command |
| ------- |
| `$ tmux list-keys` |
| `: list-keys` |

## Show every session, window, pane, etc...
| Command |
| ------- |
| `$ tmux info` |