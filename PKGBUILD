# $Id: PKGBUILD 70523 2012-05-10 14:59:20Z lcarlier $
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=lib32-libffi
pkgver=3.0.11
pkgrel=1
pkgdesc="A portable, high level programming interface to various calling conventions (32 bits version)"
arch=('x86_64')
license=('MIT')
url="http://sourceware.org/libffi"
depends=('lib32-glibc')
checkdepends=('dejagnu')
options=('!libtool')
source=(ftp://sourceware.org/pub/libffi/libffi-${pkgver}.tar.gz)
md5sums=('f69b9693227d976835b4857b1ba7d0e3')

build() {
  cd "${srcdir}/libffi-${pkgver}"

  export CC="gcc -m32"

  ./configure --prefix=/usr \
    --libdir=/usr/lib32 --libexecdir=/usr/lib32

  make
}

check() {
  cd "${srcdir}/libffi-${pkgver}"

  make check
}

package() {
  cd "${srcdir}/libffi-${pkgver}"

  make DESTDIR="${pkgdir}" install

  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/"
  rm -r "${pkgdir}"/usr/share/{info,man}
}
