# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Mark Wagie <mark@manjaro.org>

# Contributor: slact
# Author: Daniel Christophis

pkgname=tlpui
pkgver=1.4.0
pkgrel=1
pkgdesc="A GTK user interface for TLP written in Python"
arch=('any')
url="https://github.com/d4nj1/TLPUI"
license=('GPL2')
depends=('tlp' 'python-gobject')
makedepends=('git' 'python-setuptools')
_commit=2edc2142314a7d7a01bccd87ed47c2fb95da98c2 # tag=tlpui-1.4.0
source=("$pkgname::git+$url.git#commit=$_commit"
        "$pkgname.desktop")
sha256sums=('SKIP'
            'c07939b2e8c08e649579b9f3b3144b927834229f09a8f77f7f627f789c875b99')

pkgver() {
    cd "$srcdir/$pkgname"
    git describe --tags | sed 's/^tlpui.//;s/-/./g'
}

build() {
    cd "$srcdir/$pkgname"
    python setup.py build
}

package() {
    cd "$srcdir/$pkgname"
    python setup.py install --root="$pkgdir/" --optimize=1 --skip-build

    install -Dm644 "$srcdir/$pkgname.desktop" -t \
        "$pkgdir/usr/share/applications"

    for icon_size in 16 32 48 64 128 96 128 256; do
        icons_dir=usr/share/icons/hicolor/${icon_size}x${icon_size}/apps
        install -d "$pkgdir/$icons_dir"
        install -m644 "$pkgname/icons/themeable/hicolor/${icon_size}x${icon_size}/apps/$pkgname.png" -t \
            "$pkgdir/$icons_dir"
    done

    install -Dm644 "$pkgname/icons/themeable/hicolor/scalable/apps/$pkgname.svg" -t \
        "$pkgdir/usr/share/icons/hicolor/scalable/apps"
}
