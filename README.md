## General informations

**Main server** - *Baikonour*

- ***Operating System*** : Ubuntu Server 21.10 *Impish Indri*
- ***Hypervisor*** : LXD 4.23 (containers and virtual machines)

## LXD options

The following options provide some convenience for container usage :

  - `lxcfs.pidfd` : Per-container process tracking ([What is pidfd ?](https://kernel-recipes.org/en/2019/talks/pidfds-process-file-descriptors-on-linux/))
  - `lxcfs.loadavg` : Per-container load average tracking
  - `shiftfs.enable` (require an Ubuntu host) : Enable ShiftFS for containers ([What is shiftfs ?](https://discuss.linuxcontainers.org/t/trying-out-shiftfs/5155)) 

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

## References

* LXD : https://linuxcontainers.org/lxd/
* LXD documentation : https://linuxcontainers.org/lxd/docs/master/
* netplan.io : https://netplan.io/
* Seccomp Notify (syscall interception) : https://brauner.github.io/2020/07/23/seccomp-notify.html 
* TuneD : https://tuned-project.org/
* ZFS on Linux : https://zfsonlinux.org
