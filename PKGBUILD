# Maintainer: Josh Ellithorpe <quest@mac.com

pkgname=macos-sound-theme
pkgver=1.0.0
pkgrel=1
pkgdesc='MacOS trash sounds for Linux.'
arch=(any)
url=https://github.com/zquestz/macos-sound-theme
license=(MIT)
makedepends=(
  git
  meson
)
_commit=701310f0b1e5c4893caf337677dfbedd5ea457a8
source=(macos-sound-theme::git+https://github.com/zquestz/macos-sound-theme.git#commit=${_commit})
sha256sums=('4449df89278f7892d5c8e289fc47a13e2638bd56ffb8d636ede2cf327595a8aa')

build() {
  arch-meson macos-sound-theme build
  ninja -C build
}

package() {
  DESTDIR="${pkgdir}" ninja -C build install
}
