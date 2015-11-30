pkgname=cegui
pkgver=0.8.4
_tag=0-8-4
pkgrel=10
pkgdesc="A free library providing windowing and widgets for graphics APIs/engines"
arch=('x86_64')
url="http://cegui.org.uk"
license=("MIT")
depends=('pcre' 'glew' 'expat' 'freetype2' 'libxml2' 'devil' 'freeglut' 'lua' 'silly')
makedepends=('cmake' 'python2' 'doxygen' 'ogre' 'gtk2' 'boost' 'irrlicht' 'glm' 'mesa' 'mercurial')
optdepends=("python2: python bindings"
            "ogre: ogre module"
            "gtk2: gtk2 module"
            "irrlicht: irrlicht module")
source=("hg+https://bitbucket.org/cegui/cegui#tag=v${_tag}")
md5sums=('SKIP')

build() {
  cd "$srcdir/cegui"

  sed -i "s/lib64/lib/g" CMakeLists.txt

  [[ -d build ]] && rm -r build
  mkdir build && cd build

  cmake .. \
      -DCMAKE_INSTALL_PREFIX=/usr \
      -DCEGUI_LIB_INSTALL_DIR=lib \
      -DCEGUI_BUILD_PYTHON_MODULES=OFF \
      -DPYTHON_EXECUTABLE=/usr/bin/python2

  make
}

package() {
  cd "$srcdir/cegui"/build
  make DESTDIR="${pkgdir}" install
}
