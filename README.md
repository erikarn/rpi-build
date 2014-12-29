This is adrian's experiment for building freebsd-head images for the raspberry pi.

Specific bits here:

* It's all hard-coded paths in bin/build-rpi;
* I'm trying out the non-root build/install method
* .. which involves using METALOG from install, makefs and mkimg
  from FreeBSD-HEAD to do the dirty work;

Notes:

* For now the FDT blob from FreeBSD and the uboot loader are binaries in
  git.
* .. there's a port (and an update!) coming from one of the FreeBSD arm
  developers to make the Raspberry pi uboot a package and built using
  an external cross-toolchain.  That'll replace needing the binary blobs
  there.
* .. the FDT blob is from FreeBSD-HEAD (from the "builddtb" target in the
  FreeBSD makefile system) but it unfortunately doesn't install it in
  a sane place to fetch it from (ie, it doesn't install the blob in
  the DESTDIR for some reason.)

  For now you can run the 'build-fdt' target to get the .dtb built; then
  copy it into the git repo you've checked out (in files/rpi/boot/).

Note it's an old uboot: put it in two places for now:

rpi.dtb
devtree.dat

I'll update this README when I have a more up to date uboot.

How to use this?

Read bin/rpi-build.  There's a bunch of targets.  I'll write up some
instructions later - since this is a private thing, I'm being obtuse
and unhelpful for a reason.  I'm hoping this will eventually end up
in FreeBSD-HEAD as part of nanobsd, /not/ as this standalone thing.


