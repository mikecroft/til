# Git Tips

### Stop accidental pushes to upstream
If an upstream repository needs to be added, accidental pushes can be avoided, but setting the "push" URL to an invalid URL, as follows:

```
git remote set-url --push upstream no_push
```

This will result in the following:
```
➜  payara git:(master) g remote -v
origin	git@github.com:mikecroft/Payara.git (fetch)
origin	git@github.com:mikecroft/Payara.git (push)
upstream	https://github.com/payara/Payara.git (fetch)
upstream	no_push (push)
```
