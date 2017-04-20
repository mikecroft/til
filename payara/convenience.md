# Some helpful misc bits and pieces to make life a bit nicer

### Building Payara
A couple of functions to quickly build Payara Server only (i.e. not Micro et al)

This function (added to `~/.zshrc`) will do a quick build and ignore all tests. Using `-DskipTests` will still compile tests, but this option means they won't even be compiled.
```Shell
function support_build_parallel(){
  cur=`date +%F`
  mvn clean install -PQuickBuild -Dmaven.test.skip=true -Dbuild.number=$cur
}

```

This function uses parallel threads, so build time is reduced to just 2 minutes on a desktop PC with an older i7 CPU + HDD. This seemed to work fine - the build succeeded, but I'm not sure how reliable it is.
```Shell
function support_build_parallel(){
  cur=`date +%F`
  mvn clean install -PQuickBuild -Dmaven.test.skip=true -T 2C -Dbuild.number=$cur
}
```
