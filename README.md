# Linux_File_Systems

### Ext2
* stand for second extended file system
* does not have journling features
* on flash drive and usb drive ext2 is recommended
* maximum individual file size can be from 16GB to 2TB
* maximum overall file system size is 2TB to 32TB

### Ext3
* stand for third extended file system
* starting from linux kernal 2.4.15 ext3 was available
* ext3 allows journling
* max individual file size can be from 16GB to 2TB
* there are three types of journling available in ext3
  * JOURNAL ---metadeta and contents are saved in journal
  * ORDERED ---only meta deta is saved, metadata are journaled only after writing the content on disk, this is the                  default
  * Writeback ---only metadata is saved in the journal, metadata might be journled either before and after the contents is written to the disk
* you can convert ext2 to ext3 directly without backup


### Ext4
* stand for fourth extended file system
* It was introduced in 2008.
* Starting from Linux Kernel 2.6.19 ext4 was available.
* Supports huge individual file size and overall file system size.
* Maximum individual file size can be from 16 GB to 16 TB
* Overall maximum ext4 file system size is 1 EB (exabyte). 1 EB = 1024 PB (petabyte). 1 PB = 1024 TB (terabyte).
* Directory can contain a maximum of 64,000 subdirectories (as opposed to 32,000 in ext3)
* You can also mount an existing ext3 fs as ext4 fs (without having to upgrade it).
* Several other new features are introduced in ext4: multiblock allocation, delayed allocation, journal checksum. * fast fsck, etc. All you need to know is that these new features have improved the performance and reliability of the filesystem when compared to ext3.
* In ext4, you also have the option of turning the journaling feature “off”

### XFS
* stands for Extended file system
* highly scaleable, high performance file system
* orginaly designed at silicon graphics
* default file system for red hat enterprise linux 7
* supports metadata journling which facilitate quicker crash recovery
* can be defragmented and enlarged while mounted and active
* red hat enterprise 7 supports back up and restore utilities specific for xfs
* Allocation features
  * Extent based allocation
  * stripe aware allocation policies
  * delayed allocation
  * space free allocation
 

### ReiserFS
*  ReiserFS is a general-purpose, journaled computer file system
*  ReiserFS is currently supported on Linux (without quota support)
*  Introduced in version 2.4.1 of the Linux kernel
*  it was the first journaling file system to be included in the standard kernel
*  ReiserFS is the default file system on the Elive, Xandros, Linspire, GoboLinux, and Yoper Linux distributions
*  Metadata-only journaling (also block journaling, since Linux 2.6.8), its most-publicized advantage over what was the stock Linux file system at the time, ext2.
*  Online resizing (growth only), with or without an underlying volume manager such as LVM. Since then, Namesys has also provided tools to resize (both grow and shrink) ReiserFS file systems offline.
*  Tail packing, a scheme to reduce internal fragmentation. Tail packing, however, can have a significant performance impact. Reiser4 may have improved this by packing tails where it does not hurt performance


### Creating an ext2, or ext3, or ext4 filesystem
* Once you’ve partitioned your hard disk using fdisk command, use `mke2fs` to create either ext2, ext3, or ext4 file system
* Create an ext2 file system:
  * `mke2fs /dev/sda1`
* Create an ext2 file system:
  * `mkfs.ext3 /dev/sda1`

  * (or)

  * `mke2fs –j /dev/sda1`
* Create an ext4 file system:

  * `mkfs.ext4 /dev/sda1`

  * (or)

  * `mke2fs -t ext4 /dev/sda1`

### Converting ext2 to ext3

  * For example, if you are upgrading /dev/sda2 that is mounted as /home, from ext2 to ext3, do the following.

  * `umount /dev/sda2`

  * `tune2fs -j /dev/sda2`

  * `mount /dev/sda2 /home`
  
### Converting ext3 to ext4

  * If you are upgrading /dev/sda2 that is mounted as /home, from ext3 to ext4, do the following.

  * `umount /dev/sda2`

  * `tune2fs -O extents,uninit_bg,dir_index /dev/sda2`

  * `e2fsck -pf /dev/sda2`

  * `mount /dev/sda2 /home`

### Journling
* is a dedicated area in the file system, where all the changes are tracked, when the system crashes the possibility of file system corruption is less because of journling

### Fragmented file
*  It's a file on your computer too big to store in the place on the hard drive where it was originally created. So it gets cut up and spread out into various places. Naturally, it will take your drive longer to use the file because of the need to do multiple operations to open the file.
*  Over time, both the file and the hard disk itself become fragmented, and your computer slows down as it has to look in many different places to open a file. Disk Defragmenter is a tool that rearranges the data on your hard disk and reunites fragmented files so your computer can run more efficiently
