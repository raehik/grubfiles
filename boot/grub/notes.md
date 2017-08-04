GRUB notes
==========

*Author: raehik*  
*Last updated: 2017-08-04*

This document is intended to provide tips on using GRUB and booting OSs in case
you're having trouble.


Manual booting
--------------

### Linux-based

First, check the drives and partitions on offer:

    ls

Now set root, linux and initrd. Or something? TODO.

    set root=(hdX,X)
    linux /boot/vmlinuz
    initrd /boot/initrd.img


### Windows

GRUB can boot Windows by **chainloading** Microsoft's bootloader. Don't have the
commands on hand, however. TODO.


---

(empty lines follow so you don't accidentally skip things due to the pager)












