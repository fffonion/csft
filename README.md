# csft
Coreseek forked Sphinx

This is a working patch for sphinx 2.11.0-dev

For sphinx **2.11.1**, download the patch [here](https://github.com/fffonion/csft/releases/download/mmseg/csft-sphinx-2.2.11.patch)

For sphinx **2.3.2**, download the patch [here](https://github.com/fffonion/csft/releases/download/mmseg/csft-sphinx-2.3.2.patch)

### Compile

Build mmseg from [this repo](https://github.com/nzinfo/mmseg)

```shell
git clone  https://github.com/nzinfo/mmseg
cd mmseg
automake --add-missing
./bootstrap
./configure --prefix=/usr/local/mmseg
make && make install
```

Build Sphinx/Coreseek:

```shell
wget http://sphinxsearch.com/files/sphinx-2.2.11-release.tar.gz
tar zxf sphinx-2.2.11-release.tar.gz
cd sphinx-2.2.11-release
wget https://github.com/fffonion/csft/releases/download/mmseg/csft-sphinx-2.2.11.patch
patch -p1 < csft-sphinx-2.2.11.patch
sh buildconf.sh
automake --add-missing
sh buildconf.sh
./configure --prefix=/usr/local/coreseek --with-mysql \
  --with-mmseg-includes=/usr/local/mmseg/include/mmseg --with-mmseg-libs=/usr/local/mmseg/lib  
make -j$(nproc)
```

### See Also

- http://yooooo.us/2017/sphinx-with-mmseg-based-on-coreseek
