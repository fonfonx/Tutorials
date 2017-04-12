## Nvidia drivers installation

I followed the advanced instructions provided on this [Gist](https://gist.github.com/wangruohui/df039f0dc434d6486f5d4d098aa52d07) but it failed. Therefore I run the following commands

``` bash
sudo apt purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-381
#sudo systemctl stop lightdm
#sudo systemctl start lightdm
```

This requires to disable secure boot. Reboot **without secure boot**.

Check whether it works with
```
nvidia-smi
```

You must see a table with driver informations.

### Cuda installation

Go to [this page](https://developer.nvidia.com/cuda-downloads). Download the `.deb` file corresponding to your system and follow the instructions.
Make sure to still use the driver "nvidia-381" after cuda installation (go to "Softwares and Updates", then "additional drivers") You may have to reboot (in insecure mode) your computer. Check that `nvidia-smi` is still working.

In your `.bashrc` (or `.zshrc` ...) add the following lines

``` bash
export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
```

### CUDNN bindings installation

Download cudnn binding [here](https://developer.nvidia.com/rdp/cudnn-download) and put the `lib64` folder into your `LD_LIBRARY_PATH`: (I named the downloaded folder `cuda-cudnn`)
``` bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-cudnn/lib64
```

### Torch GPU support installation

If Torch is not yet installed on your system, go to [the Torch installation page](http://torch.ch/docs/getting-started.html#_) and follow the instructions. Normally the installation process will detect CUDA and install cutorch, cunn and cudnn.

Otherwise if Torch is already installed, run
``` bash
luarocks install cutorch cunn cudnn
```

To see if it worked launch Torch and import `cutorch`, `cunn` and `cudnn`:

Run `th` and
``` lua
require 'cutorch'
require 'cunn'
require 'cudnn'
```
