## Synchronise Panes

Tmux can sync commands across all panes. This can be used to send commands to multiple remote servers:

```
set-window-option synchronize-panes
```

In .tmux.conf:

```
bind-key a set-window-option synchronize-panes\; display-message "synchronize-panes is now #{?pane_synchronized,on,off}"
```

----

Tmux sets an environment variable (`$TMUX_PANE`) containing the index of each pane it creates. This can be used to connect to remote servers as follows:

```
ssh -i ~/.ssh/my_key me@remote-node$(echo $TMUX_PANE| cut -b 2).example.com
```
