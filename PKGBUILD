pkgname=uvc-gadget
pkgver=20210207
pkgrel=1
pkgdesc='UVC gadget userspace sample application'
arch=('armv6h' 'armv7h' 'aarch64')
license=('GPL2')
makedepends=('git' 'gcc' 'cmake' 'linux-headers')
url='http://git.ideasonboard.org/uvc-gadget.git'
source=(
    "git://github.com/RoEdAl/${pkgname}.git"
)
md5sums=('SKIP')

pkgver() {
	cd ${srcdir}/${pkgname}
	git log -1 --format=%cd --date=short|tr -d -
}

build() {
	mkdir -p ${srcdir}/build
	cd ${srcdir}/build
	cmake -DCMAKE_INSTALL_PREFIX=/usr ../${pkgname}
	cd ${srcdir}
	cmake --build build --clean-first
}

package() {
	cmake --build "${srcdir}/build" -- DESTDIR="${pkgdir}" install
}
