# Maintainer: ValHue <vhuelamo at gmail dot com>
#
# Contributor: ValHue <vhuelamo at gmail dot com>
#
_pkgname="Shortwave"
pkgname="shortwave"
pkgver="1.1.1"
pkgrel="5"
epoch="1"
pkgdesc="Find and listen to internet radio stations."
arch=('any')
url="https://gitlab.gnome.org/World/${_pkgname}"
license=('GPL3')
depends=('gst-plugins-bad' 'libhandy' 'libsoup' 'gtk3')
makedepends=('cargo' 'git' 'gobject-introspection' 'gst-plugins-base-libs' 'libdazzle' 'meson' 'rust')
options=('!emptydirs')
source=("${pkgname}-${pkgver}.tar.xz::${url}/uploads/df12909bb42afbff933e45da0f220eb4/${pkgname}-${pkgver}.tar.xz")
sha256sums=('dfac0dbc5f0026ec94a83bf3af3f44a02a234c93eedb5943963290536f22be47')

build() {
    cd "${pkgname}-${pkgver}"
    arch-meson builddir --prefix=/usr
    ninja -C builddir
}

check() {
    cd "${pkgname}-${pkgver}"
    ninja -C builddir test
}

package() {
    cd "${pkgname}-${pkgver}"
    DESTDIR="${pkgdir}" ninja -C builddir install

    install -D -m644 COPYING.md "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim: set ts=4 sw=4 et syn=sh ft=sh:
