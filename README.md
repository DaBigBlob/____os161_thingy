# thing thing

```sh
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

# go to os161/root
sys161 kernel
os161-prompt> p testbin/test
```



