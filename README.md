## General informations

* **Operating System** : Ubuntu 21.10 Server
* **Hypervisor** : LXD 4.18 (system containers and virtual machines manager)

## Reminders

* Create custom LXD SNAT network:

  ```shell
  $ lxc network create lxdbr0 --type=bridge ipv4.address=192.168.122.1/24 ipv4.dhcp.ranges=192.168.122.10-192.168.122.254 ipv4.nat=true ipv6.address=none dns.domain=home.lab
  ```

## Useful LXD options to enable

* `lxcfs.pidfd` : Per-container process tracking ([What is pidfd ?](https://kernel-recipes.org/en/2019/talks/pidfds-process-file-descriptors-on-linux/))
* `lxcfs.loadavg` : Per-container load average tracking
* `shiftfs.enable` (require an Ubuntu host) : Enable ShiftFS for containers ([What is shiftfs ?](https://discuss.linuxcontainers.org/t/trying-out-shiftfs/5155)) 

To enable these options :

```shell
$ snap set lxd shiftfs.enable=true
$ snap set lxd lxcfs.loadavg=true
$ snap set lxd shiftfs.enable=true

$ systemctl restart snap.lxd.daemon.service
```

## References

* LXD : https://linuxcontainers.org/lxd/
* LXD documentation : https://linuxcontainers.org/lxd/docs/master/
* TuneD : https://tuned-project.org/
* Kernel documentation :
  * sysctl : https://www.kernel.org/doc/Documentation/sysctl/
* ZFS on Linux : https://zfsonlinux.org
