# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Mark Wagie <mark at manjaro dot org>

# Contributor: slact
# Author: Daniel Christophis

pkgname=tlpui
pkgver=1.5.0.7
pkgrel=2
pkgdesc="A GTK user interface for TLP written in Python"
arch=('any')
url="https://github.com/d4nj1/TLPUI"
license=('GPL2')
depends=('tlp' 'python-gobject')
makedepends=('git' 'python-setuptools')
_commit=e6a2e9391b8068da056234fc1beec00ceb889dd8 # tag/tlpui-1.5.0-7^0
source=("git+https://github.com/d4nj1/TLPUI.git#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/TLPUI"
  git describe --tags | sed 's/^tlpui.//;s/-/./g'
}

build() {
  cd "$srcdir/TLPUI"
  python setup.py build
}

package() {
  cd "$srcdir/TLPUI"
  python setup.py install --root="$pkgdir" --optimize=1 --skip-build

  for icon_size in 16 32 48 64 128 96 128 256; do
    icons_dir=usr/share/icons/hicolor/${icon_size}x${icon_size}/apps
    install -d "$pkgdir/${icons_dir}"
    install -m644 "$pkgname/icons/themeable/hicolor/${icon_size}x${icon_size}/apps/$pkgname.png" -t \
      "$pkgdir/${icons_dir}/"
  done

  install -Dm644 "$pkgname/icons/themeable/hicolor/scalable/apps/$pkgname.svg" -t \
    "$pkgdir/usr/share/icons/hicolor/scalable/apps/"
}
