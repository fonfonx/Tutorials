## Nvidia drivers installation

I followed the advanced instructions provided on this [Gist](https://gist.github.com/wangruohui/df039f0dc434d6486f5d4d098aa52d07) but it failed. Therefore I run the following commands

```
sudo apt-get purge nvidia*
sudo apt-get nvidia-367 nvidia-modprobe
sudo lightdm stop
sudo lightdm start
```

Check whether it works with
```
nvidia-smi
```

You must see a table with driver informations.

### Cuda installation

Go to [this page](https://developer.nvidia.com/cuda-downloads). Download the `.run` file corresponding to your system and follow the instructions.

### Cutorch installation

You need to have Torch installed. Then run
```
luarocks install cutorch
```

To see if it worked launch Torch and import `cutorch`:
```
th
require 'cutorch'
```
