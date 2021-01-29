# Maintainer:  https://github.com/AlexandrParkhomenko <it@52tour.ru>

_author=visipedia
_pkgname=annotation_tools
pkgname=${_pkgname}-git
pkgver=1.0
pkgrel=1
pkgdesc='Collection of tools for editing and creating COCO style datasets'
arch=(
# 'any'
  'x86_64'
)

url='https://github.com/'
license=('MIT')
# yay -S mongodb --builddir /p #select bin package: mongodb-bin-4.0
# 'python-flask' 'python-pymongo'
depends=('mongodb' 'python-flask-pymongo' 'python-jinja') 
makedepends=('git' 'python')
source=("git://github.com/$_author/$_pkgname")
sha256sums=('SKIP')

prepare() {
  cd "$srcdir/$_pkgname"
  git submodule init
  git submodule update
  git fetch --tags
  # pip install Flask-PyMongo
}

# pkgver () {
#  cd "$srcdir/$_pkgname"
#  git describe --tags --long | sed -r 's/^v//;s/-RC/RC/;s/([^-]*-g)/r\1/;s/-/./g'
#}

build() {
  cd "$srcdir/$_pkgname"
  # see https://github.com/visipedia/annotation_tools/issues/20
  python setup.py build
}

check() {
  cd "$srcdir/$_pkgname"
# make test
}

package() {
  cd "$srcdir/$_pkgname"
  # INSTALL_ROOT="$pkgdir" make install
  python setup.py install --root="$pkgdir/" --skip-build --optimize=1
  install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
