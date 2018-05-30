<!-- vi: set et ts=4: -->
# unofficial Debian package for [libvarlink](https://github.com/varlink/libvarlink)

This is a proper debian package for the libvarlink tools and library

# Preparation

To be able to build the package you will a recent debian build system helpers
and a recent meson build-system (>= 0.40).

Those packages are only available in debian `buster`/`testing` and in the `stretch-backports` repository.

```bash
apt-get install dpkg-dev debhelper meson
```

# How to setup a working debian source package

These are the steps necessary to build a working
source-package you can then build with `dpkg-buildpackage -b`


## Step 1 Download source archive
This is mutually exclusive with Step 1b, and not supported anymore!

```bash
# download version defined in changelog
debian/rules get-orig-source
# download concrete version
VER=9 debian/rules get-orig-source

# move into correct structure
mv libvarlink_*.orig.tar.* ..
```

## Step 2 Create the source package

unpack the source archive and create the debian source package.
(This will overwrite this README)

```bash
tar --strip-components=1 -xf ../libvarlink_*.orig.tar.*
dpkg-buildpackage -S -d
```


## Step 3 Create the binary packages

This is not the primary focus, better tutorials are elsewhere.

Local Build would be:

```bash
dpkg-source -x libvarlink_10-1.dsc
cd libvarlink-10
dpkg-buildpackage
```
