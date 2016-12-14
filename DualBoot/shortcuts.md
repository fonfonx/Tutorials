## How to deal with several disks?

If you have several disks (e.g. HDD and SSD), you may want to dispatch your files on those disks. However if you specified a mounting point during the installation (e.g. `/dev/sda`) only one disk will be available and the other should be mounted to access their content.

### Create shortcuts

The first thing to do is to create shortcuts. Suppose that you want to put your heavy files (Pictures, Movies, ...) on your HDD. You can create the corresponding folders on your HDD and put your files inside them. Then create symbolic links pointing to those folders and move them to your `/home/<username>` directory. You have to keep the right names (Music, etc) to keep the little icons on the image folders.

However each time you reboot the links will be broken.

### Automatically mount your partitions

First of all you need to be able to identify your partitions. Run
```
sudo fdisk -l
```
This lists your partitions and you will be able to see their size.

Then run
```
sudo blkid
```
This will give you the `UUID` of each of your partitions.

Create in `/media/<username>` directories where you want to mount your partitions.

Finally open `/etc/fstab` in `sudo` mode and for each partition you want to mount at boot add a line
```
UUID=<corresponding-uuid> <dir-to-mount> <type> defaults 0 2
```
`<type>` corresponds to the type of the partition (e.g. `ext4`).
