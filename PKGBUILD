pkgname=python-numpy
pkgver=2.3.3
pkgrel=1
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
sha256sums=(ddc7c39727ba62b80dfdbedf400d1c10ddfa8eefbd7ec8dcb118be8b56d31029)

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
