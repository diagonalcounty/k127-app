# LibXDiff source as used in K127

This directory is the LibXDiff source compiled into the K127 iPad app.

## Version and origin

These files are an unmodified copy of [`src/xdiff`](https://github.com/libgit2/libgit2/tree/v1.3.1/src/xdiff) from [libgit2](https://github.com/libgit2/libgit2) tag **v1.3.1** (commit `1f5e7f9add5c8bbc602b14feaec216c8877c3c84`).

They were taken from the public libgit2 repository, not from a private project tree. The original LibXDiff library is by Davide Libenzi: [xmailserver.org/xdiff-lib.html](http://www.xmailserver.org/xdiff-lib.html).

## How K127 uses this library

K127 links [MiniGit](https://github.com/diagonalcounty/MiniGit) (pinned at [`bc14e1fdbe2eb24cf012a5776ff9759eb21bb174`](https://github.com/diagonalcounty/MiniGit/commit/bc14e1fdbe2eb24cf012a5776ff9759eb21bb174)). MiniGit does not build libgit2 or LibXDiff from source, and it does not modify these files. At that pin it downloads a prebuilt xcframework:

- URL: `https://github.com/light-tech/LibGit2-On-iOS/releases/download/v1.3.1/libgit2.xcframework.zip`
- SHA-256: `332bfb255649f2295d5530e4abed4e81803acdc6abf18a266695fdb447ca3df2`

The [LibGit2-On-iOS v1.3.1 build script](https://github.com/light-tech/LibGit2-On-iOS/blob/v1.3.1/build-libgit2-framework.sh) unpacks the official libgit2 `v1.3.1.zip` and compiles it with CMake. It does not patch `src/xdiff`.

The device slice of that xcframework (`ios-arm64/libgit2.a`) contains these LibXDiff objects, which match the `.c` files in this directory: `xdiffi.c.o`, `xemit.c.o`, `xhistogram.c.o`, `xmerge.c.o`, `xpatience.c.o`, `xprepare.c.o`, and `xutils.c.o`. (The archive also has `diff_xdiff.c.o`, which is libgit2's own wrapper around this library, not part of LibXDiff, and is not included here.)

LibXDiff is statically linked into the app as part of that xcframework.

## License

LibXDiff is licensed under the GNU Lesser General Public License, version 2.1 or later, as stated in `xdiff.h`. The full LGPL-2.1 text is in [COPYING](COPYING) and [lgpl-2.1.txt](lgpl-2.1.txt) (the text as included in libgit2 v1.3.1's `COPYING`). The vendored `src/xdiff` tree at that tag does not itself include a COPYING file, so the text is supplied here.

A written offer for K127 object files and build instructions needed to relink the app with a modified version of this library is on the [Licenses](../../licenses/) page. To request those, [open an issue](https://github.com/diagonalcounty/k127-app/issues).
