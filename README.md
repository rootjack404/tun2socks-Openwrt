# tun2socks-Openwrt

This make file just makes badvpn-tun2socks.


## Build Images and Packages

These are the instructions to build an image
for your router including the example applications:

```
git clone git://git.lede-project.org/source.git
cd source

./scripts/feeds update -a
./scripts/feeds install -a

git clone https://github.com/rootjack404/tun2socks-Openwrt
cp -rf tun2socks-Openwrt/badvpn package/
rm -rf tun2socks-Openwrt/

make defconfig
make menuconfig
```

Now select the right "Target System" and "Target Profile" for your target device.
Also select the examples you like to build:

* "Network" => "VPN" => "badvpn"

Packages are selected when there is a <*> in front of the name (hit the space bar twice).

Finally - build the image:
```
make
```

You can now flash your router using the correct image file inside ./bin/targets/. The images usually contain all build packages already.
The single *.ipk packages are located in ./bin/packages, in case you want to install them on other devices.

To install/update a package, transfer the ipk file to your target device to /tmp/ using scp.
The package can then be installed calling e.g. `opkg install badvpn_1.999.130-1_mips_24kc.ipk`.

