# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: slact
# Contributor: Mark Wagie / yochananmarqos
# Author: Daniel Christophis

_pkgname=TLPUI
pkgname=${_pkgname,,}
pkgver=r113.542fb5c
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
            'f42496aca91266d35e9a8917dd49c769a06b1acba5be19a2ad05b6c4968584e7')

pkgver() {
    cd $_pkgname
    printf "r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
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
