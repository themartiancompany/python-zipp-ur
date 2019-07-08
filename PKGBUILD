# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-zipp
pkgname=(python-zipp python2-zipp)
pkgver=0.5.2
pkgrel=1
pkgdesc="Pathlib-compatible object wrapper for zip files"
url="https://github.com/jaraco/zipp"
license=('MIT')
arch=('x86_64')
makedepends=('python-setuptools-scm' 'python2-setuptools-scm')
checkdepends=('python2-pathlib2' 'python2-contextlib2' 'python2-unittest2')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/jaraco/zipp/archive/v$pkgver.tar.gz")
sha512sums=('034b0872cce41a73509a896347eff79b681a6720fe01093355837c427cfb9bc8d4c592000ca236e5454627ff8ff48ac76b832fd1b6831f5188d3a9904c0a0fb6')

export SETUPTOOLS_SCM_PRETEND_VERSION=$pkgver

build() {
  cd zipp-$pkgver
  python setup.py build
  python2 setup.py build
}

check() {
  cd zipp-$pkgver
  python setup.py test
  python2 setup.py test
}

package_python-zipp() {
  depends=('python')

  cd zipp-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

package_python2-zipp() {
  depends=('python2')

  cd zipp-$pkgver
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
