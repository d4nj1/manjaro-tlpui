# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: slact
# Contributor: Mark Wagie / yochananmarqos
# Author: Daniel Christophis

_pkgname=TLPUI
pkgname=${_pkgname,,}
pkgver=r113.542fb5c
pkgrel=2
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
            '2590ec9086ef7966ac5415fe2c754014cf198a35bb9a8b4fa0f25ef31e6ebf87')

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
