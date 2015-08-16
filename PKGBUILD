# Maintainer: Richard Wiedenhöft <richard.wiedenhoeft@gmail.com>
pkgname=ivory-git
pkgver=98.878bd4e
pkgrel=1
pkgdesc="A Webbrowser written in vala"
url="https://www.metanoise.net/ivory"
arch=('x86_64' 'i686')
license=('GPL3')
depends=('gtk3' 'webkitgtk2')
provides=('ivory')
conflicts=('ivory')
makedepends=('cmake' 'vala' 'git' 'gettext' 'intltool')
source=("git+https://git.metanoise.net/ivory")
md5sums=('SKIP')
install=ivory.install

pkgver() {
	cd ivory
	echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
	cd ivory
	git submodule init
	git submodule update
	./configure \
		--prefix=/usr \
		--disable-desktop-update \
		--disable-icon-update \
		--disable-schema-compile
	make
}

package() {
	cd ivory
	make DESTDIR="${pkgdir}" install
}
