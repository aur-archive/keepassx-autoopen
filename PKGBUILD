# Maintainer: Etienne Perot <etienne[at]perot[dot]me>
pkgname=keepassx-autoopen
pkgver=20120430
pkgrel=2
pkgdesc="KeePassX with additional command-line switches to automatically open .kdb files."
url="http://www.keepassx.org/"
arch=('x86_64' 'i686')
license=('GPL')
depends=('qt4')
makedepends=('git' 'intltool' 'cmake')
conflicts=('keepassx', 'keepassx-git')

_gitroot="git://perot.me"
_gitname="keepassx-autoopen"

build() {
	cd $srcdir
	msg "Connecting to the GIT server...."

	if [[ -d $srcdir/$_gitname ]] ; then
		cd $_gitname
		git pull origin
		msg "The local files are updated."
	else
		git clone $_gitroot/$_gitname.git
	fi

	msg "GIT checkout done"
	msg "Starting make..."

	mv $srcdir/$_gitname $srcdir/$_gitname-build
	cd $srcdir/$_gitname-build

	cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DCMAKE_VERBOSE_MAKEFILE=ON -DWITH_GUI_TESTS=ON
	make DESTDIR=$pkgdir install

	rm -rf $srcdir/$_gitname-build
}
