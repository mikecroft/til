# Exposing the Internal Container Registry

In OCP 4.x+ Creating a new route with default settings won't work. The easiest way to create a route with proper settings is to get the registry operator to do it:

```
oc patch configs.imageregistry.operator.openshift.io/cluster --patch '{"spec":{"defaultRoute":true}}' --type=merge
```

https://docs.openshift.com/container-platform/4.4/registry/securing-exposing-registry.html
