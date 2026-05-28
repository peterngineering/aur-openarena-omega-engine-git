# Maintainer: P3te Rngineer
pkgname=openarena-omega-engine-git
pkgver=v3.3.9.r31.g5546508
pkgrel=2
pkgdesc="An unofficial fork of the Quake3e engine for OpenArena"
arch=('x86_64')
url="https://github.com/Bishop-333/OmegA-engine"
license=('GPL-2.0-or-later')
makedepends=('git' 'cmake' 'make' 'grep' 'zip' 'sdl3')
depends=('openarena' 'sdl3' 'libvorbis' 'curl' 'libxmp')
optdepends=('vulkan-driver: Run vulkan renderer')
provides=('openarena-omega-engine')
conflicts=('openarena-quake3e' 'openarena-omega-engine-bin' 'openarena-complete-git' 'openarena-git')
source=('git+https://github.com/Bishop-333/OmegA-engine'
    'openarena-omega'
    'openarena-omega.desktop'
    'openarena-omega.png'
)
sha256sums=('SKIP'
    '7a7afbd09fb18a61c32b67f99bc439a851063d80bd5a63059c62e4262ae4c44a'
    'a6aa64945ca74e073e48926a201e6c0ee21f7ccdf689e2a08abe981e62a11016'
    '942e791410a95268251a144494d09fa9f6555e847880f12ee802587aa50f4972')

pkgver() {
  	cd "${srcdir}/OmegA-engine"
	git describe --long --tags --abbrev=7 | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "${srcdir}/OmegA-engine"
  make
}

options=(!debug)

package() {
cd "${srcdir}/OmegA-engine/build/release-linux-x86_64"

install -Dm755 omega-x64 "${pkgdir}/opt/openarena/omega-x64"
install -Dm755 renderer_opengl_x86_64.so "${pkgdir}/opt/openarena/renderer_opengl_x86_64.so"
install -Dm755 renderer_vulkan_x86_64.so "${pkgdir}/opt/openarena/renderer_vulkan_x86_64.so"
install -Dm755 "$srcdir"/openarena-omega "${pkgdir}/usr/bin/openarena-omega"
install -Dm644 "$srcdir"/openarena-omega.png "$pkgdir"/usr/share/pixmaps/openarena-omega.png
install -Dm644 "$srcdir"/openarena-omega.desktop "$pkgdir"/usr/share/applications/openarena-omega.desktop
}
