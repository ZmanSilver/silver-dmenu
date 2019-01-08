# Maintainer:  Zachary Silver <zmansilver@gmail.com>

_pkgname=silver-dmenu
pkgname=$_pkgname
pkgver=4.8.12
pkgrel=1
pkgdesc="A customized clone of a generic menu for X"
url="https://github.com/ZmanSilver/silver-dmenu"
arch=('i686' 'x86_64')
license=('MIT')
depends=('sh' 'libxinerama' 'libxft')
makedepends=('git')
provides=($_pkgname)
conflicts=($_pkgname 'dmenu')
source=(https://www.dropbox.com/s/wun3ahrg7a198w6/silver-dmenu.tar.gz)
sha256sums=('c85cd051eeb4c551d08bd2f80ff2510a092e941f1c328ae501c8e8c8ef5b4e15')

prepare() {
  cd $_pkgname
  # to use a custom config.h, place it in the package directory
  if [[ -f ${SRCDEST}/config.h ]]; then
      cp "${SRCDEST}/config.h" .
  fi
}

build(){
  cd $_pkgname
  make \
    X11INC=/usr/include/X11 \
    X11LIB=/usr/lib/X11
}

package() {
  cd $_pkgname
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
