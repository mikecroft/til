# [Close a frozen SSH session e.g., if WiFi goes down](http://blog.infertux.com/2012/12/20/properly-close-a-frozen-ssh-session/)

* Type `RETURN`, followed by `~.` which is an SSH escape sequence to terminate a connection. The full list is below:

```
~?
Supported escape sequences:
  ~.  - terminate connection (and any multiplexed sessions)
  ~B  - send a BREAK to the remote system
  ~C  - open a command line
  ~R  - Request rekey (SSH protocol 2 only)
  ~^Z - suspend ssh
  ~#  - list forwarded connections
  ~&  - background ssh (when waiting for connections to terminate)
  ~?  - this message
  ~~  - send the escape character by typing it twice
(Note that escapes are only recognized immediately after newline.)
```
