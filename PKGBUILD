# Maintainer: Felix Yan <felixonmars@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=zipp
pkgname="${_py}-${_pkg}"
pkgver=3.17.0
_commit=5c59b561f5b79631a846b8823d5033cc1407b511
pkgrel=1
pkgdesc="Pathlib-compatible object wrapper for zip files"
_http="https://github.com"
_ns="jaraco"
url="${_http}${_ns}/${_pkg}"
license=(
  'MIT'
)
arch=(
  'any'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  'git'
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools-scm"
  "${_py}-wheel"
)
checkdepends=(
  "${_py}-pytest"
  "${_py}-pytest-enabler"
  "${_py}-pytest-mypy"
  "${_py}-jaraco.itertools"
  "${_py}-more-itertools"
  "${_py}-big-o"
  "${_py}-pytest-ignore-flaky"
)
source=(
  "git+${url}.git#commit=${_commit}"
)
sha512sums=(
  'SKIP'
)

build() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m \
      build \
    -nw
}

check() {
  cd \
    "${_pkg}"
  pytest
}

package() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}
