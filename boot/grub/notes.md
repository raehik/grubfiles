last updated 2015-08-17
by raehik


Notes on these notes
====================

This file is meant to provide useful tips on booting and using GRUB. It covers
lots of different things, from convenient menu entries to background images
and starting the default entry immediately if no modifier key is held down.
All of these configurations should already be in my own GRUB config files, but
having more info here doesn't hurt.


Show these notes in GRUB
========================

There should be a menu entry already which you can hit Enter on and see this
file's contents. Perhaps that's the case right now! Otherwise, add this entry
to your `40_custom`:

    menuentry 'Show help' {
        cat /boot/grub/notes.md
    }


Easy shutdown/reboot
====================

Chuck these entries into your `40_custom` file (preferably the end)

    menuentry 'Restart' {
        halt
    }

    menuentry 'Poweroff' {
        reboot
    }


Hide GRUB unless a key is held down
===================================

According to some sources, the GRUB menu should stay up regardless of the value
of `GRUB_TIMEOUT` if you hold down shift while GRUB starts. However, this
doesn't happen for me. So, I added a check in `40_custom` to see whether shift
is being held down: if it is, `GRUB_TIMEOUT` is set to -1 (stay up), else
nothing changes (depends on `GRUB_TIMEOUT` value). It seems to work - and if it
doesn't, then there is no change in behaviour. Here is the code (put in
`40_custom`):

    # If holding down shift, alwaus bring up menu
    if keystatus --shift; then
        set timeout=-1
    fi


Manual booting
==============

\*nixes
-------

First, check the drives and partitions on offer:
(talk about setting by UUID instead, much better!!)

    ls

etc

    set root=(hdX,X)
    linux /boot/vmlinuz
    initrd /boot/initrd.img


Windows
-------

To boot Windows with GRUB, you've gotta chainload Microsoft's bootloader.
Perhaps surprisingly, that's probably easier done than said.
(talk about setting via UUID)






That's the end of the file! Few more lines so you don't accidentally skip
things if you're in GRUB.












