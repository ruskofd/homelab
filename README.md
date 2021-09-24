## General informations

* **Operating System** : Ubuntu 21.10 Server
* **Hypervisor** : LXD 4.18 (system containers and virtual machines manager)

## Reminders

* Create custom LXD SNAT network:

  ```shell
  $ lxc network create lxdbr0 --type=bridge ipv4.address=192.168.122.1/24 ipv4.dhcp.ranges=192.168.122.10-192.168.122.254 ipv4.nat=true ipv6.address=none dns.domain=home.lab
  ```

## References

* LXD : https://linuxcontainers.org/lxd/
* LXD documentation : https://linuxcontainers.org/lxd/docs/master/
* Kernel documentation :
  * sysctl : https://www.kernel.org/doc/Documentation/sysctl/
* ZFS on Linux : https://zfsonlinux.org
