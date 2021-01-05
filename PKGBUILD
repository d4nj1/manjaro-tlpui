# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Mark Wagie <mark@manjaro.org>

# Contributor: slact
# Author: Daniel Christophis

pkgname=tlpui
pkgver=1.3.1.4
pkgrel=1
pkgdesc="A GTK user interface for TLP written in Python"
arch=('any')
url="https://github.com/d4nj1/TLPUI"
license=('GPL2')
depends=('tlp' 'python-gobject')
makedepends=('git' 'python-setuptools')
_commit='b5104d9b3a8078319fc1d04967c1826c58575dac' # tag=tlpui-1.3.1-4
source=("$pkgname::git+$url.git#commit=$_commit"
        "$pkgname.desktop")
sha256sums=('SKIP'
            'd96ecaac5512ccb7ba5fa15601c65a9092fb350519961ed1fba70a0c103e3876')

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
    export PYTHONHASHSEED=0
    python setup.py install --root="$pkgdir/" --optimize=1 --skip-build

    install -Dm644 "$srcdir/$pkgname.desktop" -t \
        "$pkgdir/usr/share/applications"
}
