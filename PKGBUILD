# Maintainer: Alexander Nicholi <me@nicholatian.com>
pkgname=unilib
pkgver=1.2.0
pkgrel=1
epoch=
pkgdesc='unilib, the ANSI C support library'
arch=('i686' 'x86_64')
url="https://github.com/aquefir/$pkgname"
license=('BSD')
depends=()
makedepends=('slick>=1.1.0')
provides=("$pkgname")
conflicts=("$pkgname")
_symver=1.1.0
source=("https://github.com/aquefir/$pkgname/archive/v${_symver}-$pkgver.tar.gz")
sha1sums=('14440199c1c8c7327d44d67e4016a59c12e62f1f')

_subprojects='arr chkmath decl endian err futils himem log str'

build() {
  cd "$srcdir/$pkgname-${_symver}-$pkgver"
  for _subproj in ${_subprojects}; do
    cd "${_subproj}"
    make -j$(($(nproc) * 2))
    cd ..
  done
}

package() {
  cd "$srcdir/$pkgname-${_symver}-$pkgver"

  for _subproj in ${_subprojects}; do
    cd "${_subproj}"
    make install PREFIX="${pkgdir}/usr"
    cd ..
  done
}
