# $Id: PKGBUILD 113591 2014-06-26 09:15:57Z lcarlier $
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=lib32-libffi
pkgver=3.1
pkgrel=1
pkgdesc="A portable, high level programming interface to various calling conventions (32-bit)"
arch=('x86_64')
license=('MIT')
url="http://sourceware.org/libffi/"
depends=('lib32-glibc')
checkdepends=('dejagnu')
source=(ftp://sourceware.org/pub/libffi/libffi-${pkgver}.tar.gz
        0001-Fix-paths-in-libffi.pc.in.patch)
sha1sums=('cb373ef2115ec7c57913b84ca72eee14b10ccdc3'
          '85b406c5208a7b8fdba9c8a4782ab524f5c5eec4')

prepare() {
  cd libffi-${pkgver}
  patch -p1 -i ../0001-Fix-paths-in-libffi.pc.in.patch
}

build() {
  cd libffi-${pkgver}

  export CC="gcc -m32"

  ./configure --prefix=/usr \
    --libdir=/usr/lib32 --libexecdir=/usr/lib32 \
    --disable-static

  make
}

check() {
  make -C libffi-${pkgver} check
}

package() {
  cd libffi-${pkgver}

  make DESTDIR="${pkgdir}" install

  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/"
  rm -r "${pkgdir}"/usr/share/{info,man}
}
