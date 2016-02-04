[![Build Status](https://travis-ci.org/libbitcoin/libbitcoin-network.svg?branch=master)](https://travis-ci.org/libbitcoin/libbitcoin-network)

[![Coverage Status](https://coveralls.io/repos/libbitcoin/libbitcoin-network/badge.svg)](https://coveralls.io/r/libbitcoin/libbitcoin-network)

# Libbitcoin Network

*Bitcoin P2P Network Library*

**License Overview**

All files in this repository fall under the license specified in [COPYING](COPYING). The project is licensed as [AGPL with a lesser clause](https://wiki.unsystem.net/en/index.php/Libbitcoin/License). It may be used within a proprietary project, but the core library and any changes to it must be published online. Source code for this library must always remain free for everybody to access.

**About Libbitcoin**

The libbitcoin toolkit is a set of cross platform C++ libraries for building bitcoin applications. The toolkit consists of several libraries, most of which depend on the foundational [libbitcoin](https://github.com/libbitcoin/libbitcoin) library. Each library's repository can be cloned and built using common [automake](http://www.gnu.org/software/automake) 1.14+ instructions. There are no packages yet in distribution however each library includes an installation script (described below) which is regularly verified in the automated build.

**About Libbitcoin Network**

Libbitcoin Network is a partial implementation of the Bitcoin P2P network protocol. Excluded are all protocols that require access to a blockchain. The [libbitcoin-node](https://github.com/libbitcoin/libbitcoin-node) library extends the P2P networking capability and incorporates [libbitcoin-blockchain](https://github.com/libbitcoin/libbitcoin-blockchain) in order to implement a full node. The [libbitcoin-explorer](https://github.com/libbitcoin/libbitcoin-explorer) library uses the P2P networking capability to post transactions to the P2P network.

## Installation

On Linux and Macintosh libbitcoin is built using Autotools as follows.
```sh
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
$ sudo ldconfig
```
Detailed instructions are provided below.

  * [Debian/Ubuntu](#debianubuntu)
  * [Macintosh](#macintosh)
  * [Windows](#windows)

### Debian/Ubuntu

Libbitcoin requires a C++11 compiler, currently minimum [GCC 4.8.0](https://gcc.gnu.org/projects/cxx0x.html) or Clang based on [LLVM 3.5](http://llvm.org/releases/3.5.0/docs/ReleaseNotes.html).

To see your GCC version:
```sh
$ g++ --version
```
```
g++ (Ubuntu 4.8.2-19ubuntu1) 4.8.2
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```
If necessary, upgrade your compiler as follows:
```sh
$ sudo apt-get install g++-4.8
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.8 50
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.8 50
$ sudo update-alternatives --install /usr/bin/gcov gcov /usr/bin/gcov-4.8 50
```
Next install the [build system](http://wikipedia.org/wiki/GNU_build_system) (Automake minimum 1.14):
```sh
$ sudo apt-get install build-essential autoconf automake libtool pkg-config
```
Next install the [Boost](http://www.boost.org) (minimum 1.55.0 for GCC or 1.54.0 for Clang) development package:
```sh
$ sudo apt-get install libboost-all-dev
```
Next download the [install script](https://github.com/libbitcoin/libbitcoin/blob/version2/install.sh) and enable execution:
```sh
$ wget https://raw.githubusercontent.com/libbitcoin/libbitcoin/version2/install.sh
$ chmod +x install.sh
```
Finally, install libbitcoin:
```sh
$ sudo ./install.sh
```
Libbitcoin is now installed in `/usr/local/`.

### Macintosh

The OSX installation differs from Linux in the installation of the compiler and packaged dependencies. Libbitcoin supports both [Homebrew](http://brew.sh) and [MacPorts](https://www.macports.org) package managers. Both require Apple's [Xcode](https://developer.apple.com/xcode) command line tools. Neither requires Xcode as the tools may be installed independently.

Libbitcoin compiles with Clang on OSX and requires C++11 support. Installation has been verified using Clang based on [LLVM 3.5](http://llvm.org/releases/3.5.0/docs/ReleaseNotes.html). This version or newer should be installed as part of the Xcode command line tools.

To see your Clang/LLVM  version:
```sh
$ clang++ --version
```
```
Apple LLVM version 6.0 (clang-600.0.54) (based on LLVM 3.5svn)
Target: x86_64-apple-darwin14.0.0
Thread model: posix
```
If required update your version of the command line tools as follows:
```sh
$ xcode-select --install
```

#### Using Homebrew

First install Homebrew. Installation requires [Ruby](https://www.ruby-lang.org/en) and [cURL](http://curl.haxx.se), which are pre-installed on OSX.
```sh
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
You may encounter a prompt to install the Xcode command line developer tools, in which case accept the prompt.

Next install the [build system](http://wikipedia.org/wiki/GNU_build_system) (Automake minimum 1.14) and [wget](http://www.gnu.org/software/wget):
```sh
$ brew install autoconf automake libtool pkgconfig wget
```
Next install the [Boost](http://www.boost.org) (1.54.0 or newer) development package:
```sh
$ brew install boost
```
Next download the [install script](https://github.com/libbitcoin/libbitcoin-network/blob/master/install.sh) and enable execution:
```sh
$ wget https://raw.githubusercontent.com/libbitcoin/libbitcoin-network/master/install.sh
$ chmod +x install.sh
```
Finally install libbitcoin:
```sh
$ ./install.sh
```
Libbitcoin is now installed in `/usr/local/`.

#### Using MacPorts

First install [MacPorts](https://www.macports.org/install.php).

Next install the [build system](http://wikipedia.org/wiki/GNU_build_system) (Automake minimum 1.14) and [wget](http://www.gnu.org/software/wget):
```sh
$ sudo port install autoconf automake libtool pkgconfig wget
```
Next install the [Boost](http://www.boost.org) (1.54.0 or newer) development package. The `-` options remove MacPort defaults that are not Boost defaults:
```sh
$ sudo port install boost -no_single -no_static -python27
```
Next download the [install script](https://github.com/libbitcoin/libbitcoin-network/blob/master/install.sh) and enable execution:
```sh
$ wget https://raw.githubusercontent.com/libbitcoin/libbitcoin-network/master/install.sh
$ chmod +x install.sh
```
Finally install libbitcoin:
```sh
$ ./install.sh
```
Libbitcoin is now installed in `/usr/local/`.

#### Notes

The install script itself is commented so that the manual build steps for each dependency can be inferred by a developer.

You can run the install script from any directory on your system. By default this will build libbitcoin-network in a subdirectory named `build-libbitcoin-network` and install it to `/usr/local/`. The install script requires `sudo` only if you do not have access to the installation location, which you can change using the `--prefix` option on the installer command line.

The build script clones, builds and installs two unpackaged repositories, namely:

- [libbitcoin/libbitcoin](https://github.com/libbitcoin/libbitcoin)
- [libbitcoin/libbitcoin-network](https://github.com/libbitcoin/libbitcoin-network)

The script builds from the head of their `master` branches. The `master` branch is a staging area for changes. The version branches are considered release quality, although this repository is not yet released as such (pending `version3`).

#### Build Options

Any set of `./configure` options can be passed via the build script, for example:
```sh
$ ./install.sh CFLAGS="-Og -g" --prefix=/home/me/myprefix
```

#### Testnet

Libbitcoin no longer requires conditional compilation for testnet.

#### Building Boost

The installer can download and install Boost. This is a large dependency that is not typically preinstalled at a sufficient level. It is recommended to use a prefix directory when building Boost.
```sh
$ ./install.sh --build-boost --prefix=/home/me/myprefix
```

### Windows

Visual Studio solutions are maintained for all libbitcoin libraries and dependencies.

> The libbitcoin execution environment supports `Windows XP Service Pack 2` and newer.

#### Upgrade Compiler

Libbitcoin requires a C++11 compiler, which means **Visual Studio 2013** minimum. Additionally a pre-release compiler must be installed as an update to Visual Studio. Download and install the following tools as necessary. Both are available free of charge:

* [Visual Studio 2013 Express](http://www.visualstudio.com/en-us/products/visual-studio-express-vs.aspx)
* [November 2013 CTP Compiler](http://www.microsoft.com/en-us/download/details.aspx?id=41151)

#### Create Local NuGet Repository

Dependencies apart from the libbitcoin libraries are available as [NuGet packages](https://www.nuget.org/packages?q=evoskuil). The libbitcoin solution files are configured with references to these packages. To avoid redundancies these references expect a [NuGet.config](http://docs.nuget.org/docs/release-notes/nuget-2.1) in a central location.

The required set of NuGet packages can be viewed using the [NuGet package manager](http://docs.nuget.org/docs/start-here/managing-nuget-packages-using-the-dialog) from the libbitcoin solution. The NuGet package manager will automatically download missing packages, either from the build scripts or after prompting you in the Visual Studio environment. For your reference these are the required packages:

* Packages maintained by [sergey.shandar](http://www.nuget.org/profiles/sergey.shandar)
 * [boost](http://www.nuget.org/packages/boost)
 * [boost\_chrono-vc120](http://www.nuget.org/packages/boost_chrono-vc120)
 * [boost\_date\_time-vc120](http://www.nuget.org/packages/boost_date_time-vc120)
 * [boost\_filesystem-vc120](http://www.nuget.org/packages/boost_filesystem-vc120)
 * [boost\_locale-vc120](http://www.nuget.org/packages/boost_locale-vc120)
 * [boost\_program\_options-vc120](http://www.nuget.org/packages/boost_program_options-vc120)
 * [boost\_regex-vc120](http://www.nuget.org/packages/boost_regex-vc120)
 * [boost\_system-vc120](http://www.nuget.org/packages/boost_system-vc120)
 * [boost\_unit\_test\_framework-vc120](http://www.nuget.org/packages/boost_unit_test_framework-vc120)

#### Build Libbitcoin Projects

After cloning the the repository the libbitcoin build can be performed manually (from within Visual Studio) or using the `buildall.bat` script provided in the `builds\msvc\build\` subdirectory. The scripts automatically download the required NuGet packages.

> Tip: The `buildall.bat` script builds *all* valid configurations. The build time can be significantly reduced by disabling all but the desired configuration in `buildbase.bat`.

> The libbitcoin dynamic (DLL) build configurations do not compile, as the exports have not yet been fully implemented. These are currently disabled in the build scripts but you will encounter numerous errors if you build then manually.
