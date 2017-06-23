# Maintainer: David Manouchehri
# Contributor: Alex Palaistras <alex+archlinux@deuill.org>

_pkgname=binaryninja
_branch=dev
_edition=personal
pkgname="${_pkgname}-${_edition}-${_branch}"
pkgdesc="Binary Ninja is a binary multi-tool and reversing platform"
url="https://binary.ninja"
license=('custom:Binary Ninja License Agreement')
arch=('x86_64')
conflicts=("${_pkgname}")
provides=("${_pkgname}")

# https://binary.ninja/recover/
source=("file://BinaryNinja-${_edition}-${_branch}.zip"
		"binaryninja-${_edition}-${_branch}"
		"binaryninja-${_branch}.png"
		"binaryninja-${_edition}-${_branch}.desktop"
		"libpython2.7.so.1")

# https://binary.ninja/js/hashes.js
sha256sums=('SKIP' # @TODO: Fetch the hash from.. somewhere?
			'6e74aae25261e7a37f9d1982b3604bd201182c69b1985ea5d5c55befb56b476a'
			'ac2e652f617d5ef8aaa34a5113164f51f3f673c872a635d29c93878a00650bf8'
			'36aea5c3f72563703b937b98381195de01084fcddacd6e4a3ed4bc48ae75c9a2'
			'SKIP')

# @TODO: Figure out what's really needed.
depends=('libcurl-compat')
makedepends=('git')
pkgver=0.1
pkgrel=1

# pkgver() {
# 	# @TODO: Use https://binary.ninja/js/changelog.js and
# 	# https://binary.ninja/js/hashes.js to bump the version automatically. 
# }

package() {
	cd "${srcdir}/${_pkgname}"
	mkdir "${pkgdir}/opt"
	mkdir -p "${pkgdir}/usr/share/icons/hicolor/128x128/apps"
	mkdir -p "${pkgdir}/usr/share/applications"
	mkdir -p "${pkgdir}/usr/bin"

	mv "${srcdir}/binaryninja" "${pkgdir}/opt/binaryninja-${_edition}-${_branch}"

	install -m644 "${srcdir}/binaryninja-${_branch}.png" "${pkgdir}/usr/share/icons/hicolor/128x128/apps/"
	install -m644 "${srcdir}/binaryninja-${_edition}-${_branch}.desktop" "${pkgdir}/usr/share/applications/"
	install -m755 "${srcdir}/binaryninja-${_edition}-${_branch}" "${pkgdir}/usr/bin"

	mv "${srcdir}/libpython2.7.so.1" "${pkgdir}/opt/binaryninja-${_edition}-${_branch}/plugins/libpython2.7.so.1"
	# ln -s "/usr/lib/libpython2.7.so" "${pkgdir}"/opt/binaryninja-${_edition}-${_branch}/libpython2.7.so.1
}

# vim:set et sw=2 sts=2 tw=80:
