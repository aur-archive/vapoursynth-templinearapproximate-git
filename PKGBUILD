# Maintainer:  Gustavo Alvarez <sl1pkn07@gmail.com>

_plug=templinearapproximate
pkgname=vapoursynth-${_plug}-git
pkgver=r1.2.g162f265
pkgrel=1
pkgdesc="Plugin for Vapoursynth: ${_plug} (GIT version)"
arch=('i686' 'x86_64')
url="https://bitbucket.org/mystery_keeper/${_plug}-vapoursynth"
license=('LGPL2.1')
depends=('vapoursynth')
provides=("vapoursynth-${_plug}")
conflicts=("vapoursynth-${_plug}" "vapoursynth-plugin-${_plug}")
makedepends=('git')
source=("${_plug}::git+https://bitbucket.org/mystery_keeper/${_plug}-vapoursynth.git")
md5sums=('SKIP')
_gitname="${_plug}"

pkgver() {
  cd "${_gitname}"
  echo "$(git describe --long --tags | tr - .)"
}

prepare() {
  cd "${_gitname}"
  echo "all:
	  gcc -shared -fPIC -o "${_plug}.so" src/main.c -I/usr/include/vapoursynth" > Makefile
}

build() {
  cd "${_gitname}"
  make
}

package(){
  cd "${_gitname}"
  install -Dm755 "${_plug}.so" "${pkgdir}/usr/lib/Vapoursynth/${_plug}.so"
  install -Dm644 MCDenoise.py "${pkgdir}/usr/lib/python3.3/site-packages/MCDenoise.py"
  install -Dm644 TempLinearApproximate-readme.txt "${pkgdir}/usr/share/doc/vapoursynth/plugins/${_plug}/README"
}
