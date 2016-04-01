pkgname=speed-dreams
pkgver=2.2.0_r6381
pkgrel=1
pkgdesc="A racing simulator with rich graphics and physics"
arch=('x86_64')
url="http://speed-dreams.sourceforge.net/"
license=('GPL2')
depends=('sdl2' 'freealut' 'freeglut' 'libpng' 'libxi' 'libxmu' 'libxrandr' 'plib' 'libjpeg-turbo' 'zlib' 'enet' 'libvorbis' 'tar' 'glu' 'openscenegraph')
makedepends=('cmake' 'tar' 'mesa')
source=("http://downloads.sourceforge.net/sourceforge/${pkgname}/${pkgname}-src-base-${pkgver/_/-}.tar.xz"
        "http://downloads.sourceforge.net/sourceforge/${pkgname}/${pkgname}-src-unmaintained-${pkgver/_/-}.tar.xz"
        "http://downloads.sourceforge.net/sourceforge/${pkgname}/${pkgname}-src-wip-cars-and-tracks-${pkgver/_/-}.tar.xz"
        "http://downloads.sourceforge.net/sourceforge/${pkgname}/${pkgname}-src-hq-cars-and-tracks-${pkgver/_/-}.tar.xz"
        "http://downloads.sourceforge.net/sourceforge/${pkgname}/${pkgname}-src-more-hq-cars-and-tracks-${pkgver/_/-}.tar.xz"
        "${pkgname}.desktop")
md5sums=('fd93042ff7c68d85e121165712c5fe43'
         'c80ec7c64d3954c1eca2f8d94d9961af'
         'b13f3d8f209d0b9f64256a14393a2812'
         'ecd7dc65a679502e376b4800a5b0fe41'
         '85214b13f1ac0aced717d456bea2605c'
         'c9ed370593ac35427ede8a5160af1969')

build() {
	msg "\033[31;1m NOTE THAT THE DISK SPACE REQUIRED TO BUILD THIS PACKAGE IS ABOUT 7GB. KCP USE A SUBFOLDER ON /tmp AS BUILD DIR COULD THUS CAUSE BUILD PROBLEMS! THEREFORE IR IS RECOMMENDED TO INSTALL WITH: 'kcp -g speed-dreams && cd ./speed-dreams && makepkg -si' IN A DIRECTORY ON A PARTITION WITH ENOUGH DISK SPACE. \033[0m"
  cmake . \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DSD_BINDIR=/usr/bin \
    -DSD_DATADIR=/usr/share/speed-dreams-2 \
    -DSD_LIBDIR=/usr/lib/speed-dreams-2 \
    -DOPTION_OFFICIAL_ONLY=ON
  make
}

package() {
  make DESTDIR="${pkgdir}/" install
  install -Dm644 "data/data/icons/icon.png" "${pkgdir}/usr/share/pixmaps/speed-dreams.png"
  install -Dm644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications/speed-dreams.desktop"
  mkdir -p "${pkgdir}/usr/share/doc/${pkgname}"
  cp -r doc/* "${pkgdir}/usr/share/doc/${pkgname}/"
  cd "${pkgdir}/usr/bin"
  ln -s speed-dreams-2 speed-dreams
}
