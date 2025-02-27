# thing thing

```sh
# clone and get into dir
git clone "https://github.com/DaBigBlob/____os161_thingy.git"
cd ____os161_thingy

# get a fresh containger and mount this directory as ~/os161/src inside container
docker run --mount type=bind,source="$(pwd)",target=/root/os161/src -ti --platform linux/amd64 eribeirofit/cse4001:lates

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
./conf DUMBVM
cd ../compile/DUMBVM
bmake depend -j33 #pretty fast on M* Macs
bmake -j33
bmake install

# go to ~/os161/root and run it
cd ~/os161/root
sys161 kernel
os161-prompt> p testbin/test # to be run in os161 prompt
```



