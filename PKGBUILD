# Merged with official ABS kimageannotator PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: dracorp aka Piotr Rogoza <piotr.r.public at gmail.com>

pkgname=kimageannotator-git
pkgver=0.5.0_r916.g6806a0b
pkgrel=1
pkgdesc='Tool for annotating images'
arch=($CARCH)
url='https://github.com/ksnip/kImageAnnotator'
license=(GPL)
depends=(qt5-svg kcolorpicker-git)
makedepends=(git cmake qt5-tools)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
source=("git+https://github.com/ksnip/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'project(kImageAnnotator' CMakeLists.txt | sed 's/.* //g' | tr - .)"
  echo "${_ver%)}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DBUILD_SHARED_LIBS=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

