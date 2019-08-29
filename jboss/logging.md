## Enable `DEBUG` logging on the given packages with a Bash script

```bash
## declare an array of packages to log on
declare -a arr=("org.jboss.as.ejb3.pool"
      "org.jboss.as.ejb3.subsystem"
      "org.jboss.as.ejb3.context"
      "org.jboss.as.ejb3.component.session"
      "org.jboss.as.ejb3.component.pool"
      "org.jboss.as.ejb3.component.messagedriven"
      )

JBOSS_CLI="/opt/wildfly/bin/jboss-cli.sh -c --controller=$(hostname -i)"

## now loop through the above array
for i in "${arr[@]}"
do
  echo "Adding logging configuration to $i"
  $JBOSS_CLI --command="/subsystem=logging/logger=$i:add()"
  $JBOSS_CLI --command="/subsystem=logging/logger=$i:write-attribute(name=level, value=ALL)"
  $JBOSS_CLI --command="/subsystem=logging/logger=$i:add-handler(name=FILE)"
  $JBOSS_CLI --command="/subsystem=logging/logger=$i:add-handler(name=CONSOLE)"
done
```

To remove logging configuration, do the above but with the following command instead:

```bash
$JBOSS_CLI --command="/subsystem=logging/logger=$i:remove()"
```
