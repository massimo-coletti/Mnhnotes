# Useful Commands on OpenVMS

## Determine processor type

```
write sys$output F$GETSYI("ARCH_NAME")
```

On Alpha you will get "Alpha", and on Itanium "IA64".

-----------------------------

## Determine OS version

```
show system /noprocess
```

-----------------------------
