# EKS Demo

It may be useful to flush the DNS to replace the cached NLB public DNS name between two tests. Here is how to proceed on Ubuntu:

```
sudo systemd-resolve --flush-caches
```