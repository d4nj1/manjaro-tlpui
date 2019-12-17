# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: slact
# Contributor: Mark Wagie / yochananmarqos
# Author: Daniel Christophis

_pkgname=TLPUI
pkgname=${_pkgname,,}
pkgver=r110.372463b
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
    '9a085522172c8ef04d592bc8d4b0c82b49065f2dd259b312e4785cd5d3408e78')

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
