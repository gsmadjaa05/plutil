# Plutil

**plutil** is a cross-platform, drop-in replacement for Apple's plutil. The primary purpose is to allow developers to modify plist files on other systems; however, it could also be extended to allow custom encoding / decoding of plists.

This project is derived from Facebook's, now archived, [xcbuild](https://github.com/facebookarchive/xcbuild). Currently, the source is pretty raw and still carries many of the abstractions introduced for xcbuild. However, as time goes on, we expect to simplify the source to remove any, now-unnecessary, abstractions.

### Requirements

#### All platforms

- [autoconf](https://www.gnu.org/software/autoconf/), [automake](https://www.gnu.org/software/automake/), [libtool](https://www.gnu.org/software/libtool/), and [pkg-config](https://www.freedesktop.org/wiki/Software/pkg-config/).

On macOS you can install those tools with [Homebrew](https://brew.sh/): `brew install autoconf automake libtool pkg-config`.

On Windows use MSYS2 and install the required autotools packages (e.g. `pacman -S base-devel autoconf automake libtool pkgconf`).

#### Linux

###### Ubuntu 18.04

`sudo apt install libpng-dev libpng16-16 libxml2-dev pkg-config ninja-build`

###### All others

- GCC 4.8 or later. `libpng16-dev`, `zlib1g-dev`, `libxml2-dev`, and `pkg-config` are also required.

#### FreeBSD

###### FreeBSD 12.1

`pkg install png-1.6.37 libxml2-2.9.9 pkgconf-1.6.3,1 ninja-1.9.0,2 gmake-4.2.1_3`

#### OpenBSD

###### OpenBSD 6.6

`pkg_add png-1.6.37 libxml-2.9.9 pkgconf-1.6.3 ninja-1.9.0 gmake-4.2.1p4`

#### macOS

- Xcode 7 or later.

#### Windows

- Visual Studio 2015 or later, on Windows. A `zlib` DLL is also required.

### Instructions

#### All platforms

```sh
git clone --depth=1 https://github.com/gsmadjaa05/plutil
git submodule update --init
```

#### Build (autotools, all platforms)

An autotools build system installs under `/usr/local` by default and, when running inside MSYS2, will adopt `/mingw32` or `/mingw64` automatically unless you pass `--prefix`.

```sh
./autogen.sh
./configure --prefix=/mingw64   # optional; use /mingw32 for 32-bit MSYS2
make
make install
```

When running inside MSYS2, `configure` automatically adopts `$MINGW_PREFIX` or the `MSYSTEM` environment (MINGW32/MINGW64) as the default prefix if none is provided.

## Licenses

Third-party licenses are listed in the `LICENSE` document.
