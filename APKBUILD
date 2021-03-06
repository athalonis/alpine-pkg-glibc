# Maintainer: Benjamin Baessler <athlon@xunit.de>

pkgname="glibc"
pkgver="2.26"
_pkgrel="0"
pkgrel="1"
pkgdesc="GNU C Library compatibility layer"
arch="aarch64"
url="https://github.com/sgerrand/alpine-pkg-glibc"
license="GPL"
source="http://mirror.archlinuxarm.org/aarch64/core/glibc-2.26-3-aarch64.pkg.tar.xz
nsswitch.conf
ld.so.conf"
subpackages="$pkgname-bin $pkgname-dev $pkgname-i18n"
triggers="$pkgname-bin.trigger=/lib:/usr/lib:/usr/glibc-compat/lib"

package() {
  mkdir -p "$pkgdir/lib" "$pkgdir/lib64" "$pkgdir/usr/glibc-compat/lib/locale" "$pkgdir"/etc
  cp -a "$srcdir"/usr/* "$pkgdir/usr/glibc-compat/"
  cp -a "$srcdir"/etc "$pkgdir/usr/glibc-compat/"
  cp -a "$srcdir"/bin "$pkgdir/usr/glibc-compat/"
  cp "$srcdir"/nsswitch.conf "$pkgdir"/etc/nsswitch.conf
  cp "$srcdir"/ld.so.conf "$pkgdir"/etc/ld.so.conf
  rm "$pkgdir"/usr/glibc-compat/etc/rpc
  rm -rf "$pkgdir"/usr/glibc-compat/bin
  rm -rf "$pkgdir"/usr/glibc-compat/lib/gconv
  rm -rf "$pkgdir"/usr/glibc-compat/lib/getconf
  rm -rf "$pkgdir"/usr/glibc-compat/lib/audit
  rm -rf "$pkgdir"/usr/glibc-compat/share
  ln -s /usr/glibc-compat/lib/ld-linux-aarch64.so.1 ${pkgdir}/lib/ld-linux-aarch64.so.1
  ln -s /usr/glibc-compat/lib/ld-linux-aarch64.so.1 ${pkgdir}/lib64/ld-linux-aarch64.so.1
  ln -s /usr/glibc-compat/etc/ld.so.cache ${pkgdir}/etc/ld.so.cache
}

bin() {
  depends="$pkgname libgcc"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/bin "$subpkgdir"/usr/glibc-compat
}

i18n() {
  depends="$pkgname-bin"
  arch="noarch"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/share "$subpkgdir"/usr/glibc-compa
}

#https://www.archlinux.org/packages/community/any/aarch64-linux-gnu-glibc/download/

md5sums="af26654af42dd16d882cd264e258c64a  glibc-2.26-3-aarch64.pkg.tar.xz
5be984273de4203318c9c3fb0d4e9d2b  nsswitch.conf
0484678534996fdddef848544bd1a12d  ld.so.conf"
sha256sums="ddba3463a13ccbd148174a279016bdc582a3b8d29b17217b3bf366e5070d9945  glibc-2.26-3-aarch64.pkg.tar.xz
3be94785355b4b363d1268f133e198323441eafa6017b2b1fed32ae279d685c7  nsswitch.conf
f8eec838bace59c29a5dc04550f60e3c7ba9f3a9df7b14dae36349ad90152e00  ld.so.conf"
sha512sums="b168d33b930484f8e96f1f09574e5454dee1266e98c56a0ce7f2da757271db6bc7a7e4de4827b5b9b7dc1066c17a56007e45998916ec3e2252ed26eb4b33a230  glibc-2.26-3-aarch64.pkg.tar.xz
478bdd9f7da9e6453cca91ce0bd20eec031e7424e967696eb3947e3f21aa86067aaf614784b89a117279d8a939174498210eaaa2f277d3942d1ca7b4809d4b7e  nsswitch.conf
2912f254f8eceed1f384a1035ad0f42f5506c609ec08c361e2c0093506724a6114732db1c67171c8561f25893c0dd5c0c1d62e8a726712216d9b45973585c9f7  ld.so.conf"
