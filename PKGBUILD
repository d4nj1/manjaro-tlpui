# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: slact
# Author: Daniel Christophis

pkgname=tlpui
_pkgname=TLPUI
pkgver=r109.703bade
pkgrel=1
pkgdesc="A GTK-UI to change TLP configuration files easily. It has the aim to protect users from setting bad configuration and to deliver a basic overview of all the valid configuration values."
arch=('any')
url="https://github.com/d4nj1/$_pkgname"
license=('GPLv2')
depends=("tlp" "python" "pygtk" "python-gobject")
source=(git+https://github.com/d4nj1/$_pkgname.git
  "$pkgname.sh"
  "$pkgname.desktop")
md5sums=('SKIP'
         '9f23dcf973bac1089280be1255dfe34d'
         'ac5c088895666e9cdf095023acea5163')

pkgver() {
  cd $_pkgname
  printf "r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

package() {
  cd "$srcdir/$_pkgname"
  mkdir -p "$pkgdir"/opt/$pkgname
  cp -dpr --no-preserve=ownership ./ "$pkgdir"/opt/$pkgname/
  rm -Rf "$pkgdir"/opt/tlpui/$pkgname/__pycache__
  rm -Rf "$pkgdir"/opt/tlpui/$pkgname/ui_config_objects/__pycache__  
  
  install -Dm644 "$srcdir"/$pkgname.desktop "$pkgdir"/usr/share/applications/$pkgname.desktop
  install -Dm755 "$srcdir"/$pkgname.sh "$pkgdir"/usr/bin/$pkgname
}

