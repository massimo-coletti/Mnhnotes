## Run du without traversing mounted file systems
```
for i in /*; do if ! mountpoint -q "$i"; then du -sh $i; fi; done
```

-----------------------------

