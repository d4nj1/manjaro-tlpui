# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: slact
# Contributor: Mark Wagie / yochananmarqos
# Author: Daniel Christophis

_pkgname=TLPUI
pkgname=${_pkgname,,}
pkgver=1.2.r6.g945ff46
pkgrel=1
pkgdesc="A GTK user interface for TLP written in Python"
arch=('any')
url="https://github.com/d4nj1/$_pkgname"
license=('GPL2')
depends=('python-gobject'
    'tlp')
makedepends=('git'
    'python-setuptools')
source=("git+$url.git"
        "$pkgname.desktop")
sha256sums=('SKIP'
            'd96ecaac5512ccb7ba5fa15601c65a9092fb350519961ed1fba70a0c103e3876')

pkgver() {
    cd $_pkgname
    git describe --long --tags | sed 's/^tlp.//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    cd $_pkgname
    python setup.py build
}

package() {
    install -Dm644 $pkgname.desktop -t $pkgdir/usr/share/applications
    cd $_pkgname
    python setup.py install --root="$pkgdir/" --optimize=1 --skip-build
}
