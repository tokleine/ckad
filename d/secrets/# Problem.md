# Problem

# Findings:
- when updating the configmap, the symlink itself is not updated (mtime), but the underlying data is
```text
root@search-as-a-service-76c5896bc7-fq9n6:/app/configs# ls -la
total 12
drwxrwxrwx 3 root root 4096 Apr 14 12:29 .
drwxr-xr-x 1 root root 4096 Apr 14 08:48 ..
drwxr-xr-x 2 root root 4096 Apr 14 12:29 ..2025_04_14_10_29_15.3928161130
lrwxrwxrwx 1 root root   32 Apr 14 12:29 ..data -> ..2025_04_14_10_29_15.3928161130
lrwxrwxrwx 1 root root   23 Apr 14 11:57 experiments.json -> ..data/experiments.json
```