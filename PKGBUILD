pkgname=python-numpy
pkgver=2.3.4
pkgrel=2
pkgdesc="Scientific tools for Python"
arch=('x86_64')
url="https://www.numpy.org/"
license=('custom')
depends=('gcc')
makedepends=(
    'python-build'
    'python-cython'
    'python-installer'
    'python-meson-python'
    'python-pyproject-metadata')
source=(https://github.com/numpy/numpy/releases/download/v${pkgver}/${pkgname#*-}-${pkgver}.tar.gz)
sha256sums=(a7d018bfedb375a8d979ac758b120ba846a7fe764911a64465fd87b8729f4a6a)

build() {
    cd  ${pkgname#*-}-${pkgver}

    CFLAGS+=" -ffat-lto-objects"
    CXXFLAGS+=" -ffat-lto-objects"

    python3 -m build --wheel --no-isolation
}

package() {
    cd  ${pkgname#*-}-${pkgver}

    python3 -m installer -d ${pkgdir} dist/*.whl
}
