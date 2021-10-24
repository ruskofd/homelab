## General informations

* **Main server** (Baikonour):

- ***Operating System*** : Ubuntu Server 21.10 *Impish Indri*
- ***Hypervisor*** : LXD 4.19 (containers + VMs)

* **Raspberry Pi 4** (Spoutnik):

- ***Operating System*** : Ubuntu Server 21.10 *Impish Indri*
- ***Container manager*** : systemd-nspawn (systemd 248)

## LXD options

The following options provide some convenience for container usage :

* `lxcfs.pidfd` : Per-container process tracking ([What is pidfd ?](https://kernel-recipes.org/en/2019/talks/pidfds-process-file-descriptors-on-linux/))
* `lxcfs.loadavg` : Per-container load average tracking
* `shiftfs.enable` (require an Ubuntu host) : Enable ShiftFS for containers ([What is shiftfs ?](https://discuss.linuxcontainers.org/t/trying-out-shiftfs/5155)) 

Enable these options through `snap` command-line :

  ```shell
  snap set lxd lxcfs.pidfd=true
  snap set lxd lxcfs.loadavg=true
  snap set lxd shiftfs.enable=true
  ```

Then, restart the LXD daemon :

  ```
  systemctl restart snap.lxd.daemon.service
  ```

## Tips/tricks

* Create custom LXD SNAT network:

  ```shell
  lxc network create lxdbr0 --type=bridge ipv4.address=192.168.122.1/24 ipv4.dhcp.ranges=192.168.122.10-192.168.122.254 ipv4.nat=true ipv6.address=none dns.domain=home.lab
  ```

## References

* LXD : https://linuxcontainers.org/lxd/
* LXD documentation : https://linuxcontainers.org/lxd/docs/master/
* TuneD : https://tuned-project.org/
* ZFS on Linux : https://zfsonlinux.org
* Kernel documentation :
  * sysctl : https://www.kernel.org/doc/Documentation/sysctl/
* Seccomp Notify (syscall interception) : https://brauner.github.io/2020/07/23/seccomp-notify.html 
* systemd-nspawn : https://www.freedesktop.org/software/systemd/man/systemd-nspawn.html 
* mkosi : https://github.com/systemd/mkosi
* CoreDNS : https://coredns.io/
