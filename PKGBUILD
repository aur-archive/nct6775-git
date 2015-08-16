# Maintainer: Glaucous <glakke1 at gmail dot com>
pkgname=nct6775-git
pkgver=20120714
pkgrel=1
pkgdesc="New driver for Nuvoton NCT6775F, NCT6776F, NCT6779D"
arch=('x86_64' 'i686')
url="https://github.com/groeck/nct6775"
license=('GPLv3')
groups=()
depends=()
makedepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=(!ccache)
install=nct6775-git.install
changelog=
source=('header.patch')
noextract=()
md5sums=('77972acffc43a5285dff99e80100343b')

_gitroot='git://github.com/groeck/nct6775.git'
_gitname='nct6775'

_installpath="$pkgdir/usr/lib/modules/$(uname -r)/kernel/drivers/hwmon/nct6775.ko"

build() {
	cd "$srcdir"
 	msg "Connecting to GIT server...."
 	if [ -d $_gitname ] ; then
   		cd $_gitname && git pull origin
   		msg "The local files are updated."
 	else
   		git clone --depth=1 $_gitroot $_gitname
 	fi
 	msg "GIT checkout done or server timeout"

	msg "Applying patch for header path"
	patch -Np0 -i header.patch

	cd $_gitname
	make
}

package() {
	install -Dm755 $srcdir/$_gitname/nct6775.ko $_installpath
}
