# Maintainer: Your Name <your@email.com>
pkgname=gr-funcube-git
pkgver=1.0.0
pkgrel=1
pkgdesc="gr-funcube is an linux oot-module for gnuradio to implement a funcube dongle and a funcube dongle pro+"
arch=('x86_64')
url="https://github.com/amaroq74/gr-funcube"
license=('GPL')
depends=('cmake' 'gcc') # Add other dependencies as needed
makedepends=('cmake') # CMake is a build dependency

source=("https://github.com/amaroq74/gr-funcube")
sha256sums=('SKIP')

pkgver() {
  cd $_gitname
  git describe --always | sed 's|-|.|g; s|^.||'
}

build() {
  # Create a build directory and navigate into it
  mkdir -p build
  cd build

  # Configure the project with CMake
  # -DCMAKE_INSTALL_PREFIX=/usr is standard for Arch Linux packages
  # -DCMAKE_BUILD_TYPE=Release ensures an optimized build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release

  # Build the project
  cmake --build .
}

package() {
  # Navigate to the build directory
  cd build

  # Install the project into the package directory
  # DESTDIR is crucial for installing into the temporary package root
  cmake --install . --prefix=/usr --destdir="${pkgdir}"
}
