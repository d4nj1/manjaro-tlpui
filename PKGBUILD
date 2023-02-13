# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Mark Wagie <mark at manjaro dot org>

# Contributor: slact
# Author: Daniel Christophis

pkgname=tlpui
_app_id=com.github.d4nj1.tlpui
pkgver=1.5.0.6
pkgrel=1
pkgdesc="A GTK user interface for TLP written in Python"
arch=('any')
url="https://github.com/d4nj1/TLPUI"
license=('GPL2')
depends=('tlp' 'python-gobject')
makedepends=('git' 'python-setuptools')
_commit=d4fa443b35aa6c1710d518c43f51da637a1c39a9 # tag/tlpui-1.5.0-6^0
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
