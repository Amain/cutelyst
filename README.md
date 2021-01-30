# Add debian package support

See github releases for binary packages.

## Build yourself:
```bash
$ sudo apt-get install build-essential cmake qtbase5-dev uwsgi uuid-dev libcap-dev libzmq3-dev libpwquality-dev libmemcached-dev libjemalloc-dev libgrantlee5-dev pkg-config libvirt-dev clearsilver-dev doxygen graphviz quilt qttools5-dev-tools debhelper-compat qt5-default libssl-dev libpcre-dev zlib1g-dev
$ git clone https://github.com/Amain/cutelyst
$ #Update debian package version if you need to in debian/changelog (currently set to 3.0-main1)
$ dpkg-buildpackage -b -rfakeroot --no-sign
```

Notes:
* Tested on Debian 10 (Buster)
* Tested on Ubuntu 20.04
* Small patch added to allow building with qt < 5.14.2
* Following plugins disabled due to build/dependency issues (debian/rules):
  * PLUGIN_VIEW_EMAIL
  * PLUGIN_VIEW_CUTELEE
  * PLUGIN_MEMCACHED
