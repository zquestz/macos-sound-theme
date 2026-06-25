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
_commit=83d14c9f323bfa1850b7f310a0c8ba718d067be1
source=(macos-sound-theme::git+https://github.com/zquestz/macos-sound-theme.git#commit=${_commit})
sha256sums=('99de9e0a52503265727848b0ae124d0ca9917c1cda78830ec9559170149a78b2')

build() {
  arch-meson macos-sound-theme build
  ninja -C build
}

package() {
  DESTDIR="${pkgdir}" ninja -C build install
}
