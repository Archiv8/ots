#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and drián Pérez de Castro <aperez@igalia.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/ots/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/ots/discussions>

pkgname=ots
pkgver=8.2.1
pkgrel=1
pkgdesc="OpenType fonts sanitiser. Supports TTF, WOFF, WOFF2 and other formats"
arch=(
  "x86_64"
  "i686"
)
url="https://github.com/khaledhosny/ots"
license=(
  "custom"
)
depends=(
  "freetype2"
  "lz4"
  "woff2"
)
makedepends=(
  "meson"
  "ninja"
)
checkdepends=(
  "gtest"
)
source=(
  "https://github.com/khaledhosny/${pkgname}/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.xz"
)
sha512sums=(
  "8f7c7c59b167efb2ed16877fd7bc3c957d742eeeeb12faa536f93e2c1da50a6fdb6d0548f945a2f498ab11ce799e79ed2252370d524ae9e05faa319a9801caf8"
)

build() {

  cd "${pkgname}-${pkgver}"

  arch-meson build -Dgraphite=true

  ninja -C build
}

check() {

  meson test -C "${pkgname}-${pkgver}/build"
}

package() {

  cd "${pkgname}-${pkgver}"

  DESTDIR="${pkgdir}" ninja -C build install

  install -Dm0644 -t "${pkgdir}/usr/share/licenses/${pkgname}/" LICENSE
}
