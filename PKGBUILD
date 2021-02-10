# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Mark Wagie <mark@manjaro.org>

# Contributor: slact
# Author: Daniel Christophis

pkgname=tlpui
pkgver=1.3.1.8
pkgrel=1
pkgdesc="A GTK user interface for TLP written in Python"
arch=('any')
url="https://github.com/d4nj1/TLPUI"
license=('GPL2')
depends=('tlp' 'python-gobject')
makedepends=('git' 'python-setuptools')
_commit='7de3d8bbed34ea619a00fca159f14677440ffd8b' # tag=tlpui-1.3.1-8
source=("$pkgname::git+$url.git#commit=$_commit"
        "$pkgname.desktop")
sha256sums=('SKIP'
            '347fad2e6cf02d01d770b654f8b2da1f8aaa0ac37097f84ef6bc4053bd7fcae4')

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
