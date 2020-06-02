# Generating load from the CLI

## CPU load

This command generates load (`md5sum /dev/zero`) for 5 minutes (`timeout 5m`) and uses `-P0` to force `xargs` to run unlimited parallel executions of one argument (`-n1`) at a time. `seq 3` makes it do that 3 times.

```
seq 3 | xargs -P0 -n1 timeout 5m md5sum /dev/zero
```
It was [stolen from StackOverflow](https://stackoverflow.com/a/41782305).


## Memory

This command requires bash (not just `sh`) and consumes 500MiB and holds it open for 5 minutes.

```
cat <(yes | tr \\n x | head -c $((1024*1024*500))) <(sleep 5m) | grep n
```
It was [stolen from the Unix StackExchange](https://unix.stackexchange.com/a/254976).
