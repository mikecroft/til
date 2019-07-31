# List Uptime of My Java Processes

```
jps -q | xargs ps -o "user etime" -p | grep $(whoami)
```
