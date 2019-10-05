# nvf_telco_notes

Here you can find my notes on experiences and lessons learnt with telco real-time workloads:

## Enabling HugePages
Hugepages: 80GB of RAM allocated to HugePages.
Enabling PCI passthrough to enable SR-IOV on intel card.

GRUB PARAMETERS need to be reconfigured:

```
$GRUB_CMD_LINE_DEFAULT="hugepages=40000 transparent_hugepage=never default_hugepagesz=2M hugepagesz=2M"
```

Apply grub changes:

```
host01$ sudo update-grub2
host01$ sudo reboot
```

Now, check that your compute node has hugepages:

```
host01$ cat /proc/meminfo | grep Huge
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
HugePages_Total:   40000
HugePages_Free:    40000
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
```

## Enabling SR-IOV on Intel card

Map virtual memory address to physical memory allocation:

*iommu* enables mapping of virtual memory addresses to physical addresses
Edit your grub config file an append the following value to GRUB variable:

```
$GRUB_CMD_LINE_DEFAULT="intel_iommu=on"
```

Apply grub changes:

```
host01$ sudo update-grub2
host01$ sudo reboot
```
