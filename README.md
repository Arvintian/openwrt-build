Build openwrt for x86 and mt7621.

## Source code

```
git clone git@github.com:coolsnowwolf/lede.git
git checkout -b 6c4e5d7b4
git checkout 6c4e5d7b4757f11da966ae9152d04f09ded35226
```

## Feed Conf

```
cp feed.conf.default lede/feed.conf.default
```

## MT7621-Xiaomi-4A

```
cp mt7621_xiaomi_mi-router-4a-3g-v2.dtsi lede/target/linux/ramips/dts/mt7621_xiaomi_mi-router-4a-3g-v2.dtsi
cp mt7621.mk lede/target/linux/ramips/image/mt7621.mk
cp config.mt7621 lede/.config
```

## x86

```
cp config.x86 lede/.config
```


## Ubuntu

```
sudo apt update -y
sudo apt install -y ack antlr3 aria2 asciidoc autoconf automake autopoint binutils bison build-essential \
bzip2 ccache cmake cpio curl device-tree-compiler fastjar flex gawk gettext gcc-multilib g++-multilib \
git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libglib2.0-dev libgmp3-dev libltdl-dev \
libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libreadline-dev libssl-dev libtool lrzsz \
mkisofs msmtp nano ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 python3-pip libpython3-dev qemu-utils \
rsync scons squashfs-tools subversion swig texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev
```

## Build

```
./scripts/feeds update -a
./scripts/feeds install -a
make download -j8
make V=s -j1
# nohup make V=s -j1 >out.log 2>err.log &
```