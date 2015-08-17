# Maintainer: peace4all <markspost at rocketmail dot com>

pkgname=rhythmbox-remember-the-rhythm-git
_gitname="remember-the-rhythm"
pkgver=8438d0e
pkgrel=1
pkgdesc="Rhythmbox plugin to remember the last playing song and position."
url="https://github.com/owais/remember-the-rhythm"
arch=('i686' 'x86_64')
license=('GPL')
makedepends=('git')
depends=('rhythmbox>=2.9')
source=("$_gitname::git+https://github.com/owais/remember-the-rhythm.git")
md5sums=('SKIP')
install=$pkgname.install

pkgver() {
  cd "${srcdir}/${_gitname}"
  git describe --always | sed 's|-|.|g'
}

package() {
  cd "${srcdir}/${_gitname}"

  #python fix
  sed -i -e "s|Loader=python|Loader=python3|" $(find . -name '*.plugin')

  mkdir -p "$pkgdir/usr/lib/rhythmbox/plugins/$_gitname"
  mv README.rst README
  cp -R {README,AUTHORS,COPYING} "$pkgdir/usr/lib/rhythmbox/plugins/$_gitname/"
  cp -R src/{*.py,*.plugin} "$pkgdir/usr/lib/rhythmbox/plugins/$_gitname/"

  mkdir -p "$pkgdir/usr/share/glib-2.0/schemas/"
  cp -R schemas/*.gschema.xml "$pkgdir/usr/share/glib-2.0/schemas/"
}
