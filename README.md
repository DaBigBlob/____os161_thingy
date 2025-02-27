# thing thing

```sh
# clone and get into dir
git clone "https://github.com/DaBigBlob/____os161_thingy.git"
cd ____os161_thingy

# get a fresh containger and mount this directory as ~/os161/src inside container
docker run --mount type=bind,source="$(pwd)",target=/root/os161/src -ti --platform linux/amd64 eribeirofit/cse4001:latest

cd ~/os161/src
./configure
# building the userland
# only builds the clibs and testbin/test
# everything else disabled
bmake includes
bmake depend -j33 #pretty fast on M* Macs
bmake -j33
bmake install

# building the kernel
cd kern/conf
./config DUMBVM
cd ../compile/DUMBVM
bmake depend -j33 #pretty fast on M* Macs
bmake -j33
bmake install

# go to ~/os161/root and run it
cd ~/os161/root
sys161 kernel
p testbin/test # to be run in os161 prompt
```

Notice the files `kern/include/syscall.h` and `userland/include/unistd.h`.  
In `kern/include/syscall.h` we have `int sys_hello(int *y, int x);` (line 61).  
In `userland/include/unistd.h` we have `int hello(int x);` (line 154).  



