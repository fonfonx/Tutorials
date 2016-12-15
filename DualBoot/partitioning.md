## Partitioning

### Before installing

In order to partition your disk, use the Partitioning Tools provided by Windows.
On your SSD create a partition (A) for your Linux OS that should have at least 50Gb and a swap partition (B) that should have roughly 1.5 times your RAM capacity.
On your HDD create a partition for your Linux files of the size you want.

### During installation

When the Ubuntu installer asks you how you want to install Ubuntu, choose *Do something else* and:
+ choose the partition (A), format it as `ext4` and set it as a mounting point for `/`
+ choose the partition (B), format it as `swap`
+ select `/dev/sda` (your SSD) as boot disk
