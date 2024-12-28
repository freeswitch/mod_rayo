# mod_rayo

Rayo server / node implementation. Allows MxN clustering of FreeSWITCH and Rayo Clients (like Adhearsion)

## Table of Contents

* [Table of Contents](#table-of-contents)
* [Build and install mod_rayo](#build-and-install-mod_rayo)
* [Build standalone mod_rayo module using FreeSWITCH devel package](#build-standalone-mod_rayo-module-using-freeswitch-devel-package)

## Build and install mod_rayo

Change to a directory where the FreeSWITCH sources will be compiled

```
cd /usr/src
```

Clone the FreeSWITCH repository into the above directory

```
git clone https://github.com/signalwire/freeswitch.git
```

Perform an initial bootstrap of FreeSWITCH so that a `modules.conf` file is created

```
./bootstrap.sh
```

Add the mod_rayo to `modules.conf` so that an out-of-source build will be performed

```
mod_rayo|https://github.com/freeswitch/mod_rayo.git -b main
```

Configure, build and install FreeSWITCH

```
./configure
make
make install
```

The following commands will build and install *only* mod_rayo

```
make mod_rayo
make mod_rayo-install
```

To run mod_rayo within FreeSWITCH, perform the following two steps
1. Add mod_rayo to freeswitch/conf/autoload/modules.conf.xml
2. Add conf/autoload_configs/rayo.conf.xml to freeswitch/conf/autoload_configs

## Build standalone mod_rayo module using FreeSWITCH devel package

Install FreeSWITCH devel package (assuming you have [FreeSWITCH Debian repository setup](https://github.com/signalwire/freeswitch/tree/master/scripts/packaging))
```
apt-get update
apt-get install -y libfreeswitch-dev
```

Change to a directory where mod_rayo sources will be compiled
```
cd /usr/src
```

Clone mod_rayo module
```
git clone https://github.com/freeswitch/mod_rayo -b main
```

Go to the module's source folder
```
cd mod_rayo
```

And build normally
```
./bootstrap.sh
./configure
make
make install
```