# $Id: PKGBUILD 69620 2012-04-20 14:11:11Z bpiotrowski $
# Maintainer:  Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer:  Bartłomiej Piotrowski <nospam@bpiotrowski.pl>
# Contributor: Thorsten Töpper <atsutane-tu@freethoughts.de>
# Contributor: Thayer Williams <thayer@archlinux.org>
# Contributor: Jeff 'codemac' Mickey <jeff@archlinux.org>

pkgname=dmenu
pkgver=4.5
pkgrel=3
pkgdesc="A generic menu for X"
url="http://tools.suckless.org/dmenu/"
arch=('i686' 'x86_64')
license=('MIT')
depends=('sh' 'libxinerama' 'libxft')
source=(http://dl.suckless.org/tools/$pkgname-$pkgver.tar.gz)
_patches=(01-dmenu-$pkgver-filecompletion.diff)
		  #02-dmenu-$pkgver-xft.diff)
source=(${source[@]} ${_patches[@]})

build(){
  cd $srcdir/$pkgname-$pkgver

  for p in "${_patches[@]}"; do
  	echo "=> $p"
    patch < ../$p || return 1
  done

  make
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make PREFIX=/usr DESTDIR=$pkgdir install
  install -m644 -D LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
