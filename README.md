# packrat
[![CI Actions Status](https://github.com/perftool-incubator/packrat/workflows/crucible-ci/badge.svg)](https://github.com/perftool-incubator/packrat/actions)

A system information collection utility for the [crucible](https://github.com/perftool-incubator/crucible) performance testing framework.

## Purpose

Packrat captures comprehensive system and environment data from test endpoints during benchmark execution. This ensures reproducibility by documenting the exact hardware and software configuration at the time of testing.

## Usage

Packrat runs automatically as part of crucible's engine execution phase via rickshaw. It can also be run standalone:

```
./packrat <destination-directory>
```

This creates a `packrat-archive/` subdirectory containing all collected data, compressed with xz.

## Data Collected

Packrat runs 14 parallel collectors:

| Collector | Data |
|-----------|------|
| distro | OS release, tuned profiles |
| package_manager | Installed RPM packages |
| env | Environment variables, hostname, virtualization type |
| cpu | lscpu, /proc/cpuinfo, intel_pstate settings |
| device | lspci, interrupt assignments |
| system | dmidecode, lstopo |
| kernel | dmesg, uname, lsmod, sysctl, SELinux, module parameters, clocksource, IOMMU |
| block | lsblk, device-mapper, LVM, block queue settings |
| memory | meminfo, slabinfo, hugepages, transparent hugepage, NUMA node info |
| net | ifconfig, bridge, nmcli, ethtool, network device sysfs |
| cgroup | cpuset and cpu cgroup configuration |
| libvirt | virsh sysinfo, capabilities, domains, networks, pools |
| firewall | iptables, ebtables, nft, firewall-cmd |
| container | podman info, images, version |
