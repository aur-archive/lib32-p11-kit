# Maintainer: Christoph Vigano <mail@cvigano.de>

_pkgbasename=p11-kit
pkgname=lib32-$_pkgbasename
pkgver=0.9
pkgrel=2
pkgdesc="32 bit library to work with PKCS#11 modules"
arch=(i686 x86_64)
url="http://p11-glue.freedesktop.org"
license=('BSD')
depends=(lib32-glibc)
options=(!libtool)
source=($url/releases/$_pkgbasename-$pkgver.tar.gz)
md5sums=('029aa2a3a103e7eb81b4aa731b93539e')

build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"
  cd "$srcdir/$_pkgbasename-$pkgver"

  ./configure --prefix=/usr --libdir=/usr/lib32 --sysconfdir=/etc \
    --with-module-path=/usr/lib32/pkcs11
  make
}

package() {
  cd "$srcdir/$_pkgbasename-$pkgver"
  make DESTDIR="$pkgdir" install
  rm -rf "${pkgdir}"/etc
  rm -rf "${pkgdir}"/usr/{bin,include,share}
  install -Dm644 COPYING $pkgdir/usr/share/licenses/$pkgname/COPYING
}

# vim:set ts=2 sw=2 et:
