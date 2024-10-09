# Maintainer:
# Contributor: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Andrew Rabert <ar@nullsum.net>

: ${_commit:=4c2fbd264510ca588cfd24931db8d6e81990ea24} # 0.8.12

_pkgname="xboxdrv"
pkgname="$_pkgname"
pkgver=0.8.12
pkgrel=1
pkgdesc="Userspace Xbox gamepad driver and input remapper"
url="https://github.com/xiota/xboxdrv"
license=('GPL-3.0-or-later')
arch=('x86_64')

depends=(
  'python'
  'dbus-glib'
  'dbus-python'
  'libusb'
  'libx11'
)
makedepends=(
  'git'
  'glib2-devel'
  'meson'
  'ninja'
)

options=('!debug')

backup=("etc/default/xboxdrv")

_pkgsrc="$_pkgname"
source=("$_pkgsrc"::"git+$url.git#commit=$_commit")
sha256sums=('SKIP')

build() {
  arch-meson build "$_pkgsrc"
  meson compile -C build
}

package() {
  meson install -C build --destdir "$pkgdir"
}
