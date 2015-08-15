#Maintainer: hbdee <hbdee.arch@gmail.com>

pkgname=cantata-kde
_pkgname=cantata
pkgver=1.5.2
pkgrel=1
pkgdesc="KDE client for the music player daemon (MPD)"
arch=('i686' 'x86_64')
url="https://code.google.com/p/cantata/"
license=('GPL')
depends=('kdebase-runtime' 'libmtp' 'libcddb' 'libmusicbrainz5' 'mpg123' 'taglib-extras' 'hicolor-icon-theme' 'cdparanoia' 'speexdsp' 'media-player-info')
optdepends=('perl-uri: dynamic playlist'
            'mpd: playback')
makedepends=('cmake' 'automoc4')
conflicts=('cantata' 'cantata-svn' 'cantata-kde-svn')
provides=('cantata')
install="$pkgname.install"
source=("$_pkgname-$pkgver.tar.bz2::https://drive.google.com/uc?export=download&id=0Bzghs6gQWi60LV9rM3RMQk85Z1E")
md5sums=('0b29d30f1b03ecac23eb608309fbeaa1')

prepare() {
  if [[ -d build ]]
  then
    rm -rf build
  fi
   mkdir build
}

build() {
  cd "$srcdir/build"

  cmake ../${_pkgname}-${pkgver} \
    -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` \
    -DCMAKE_BUILD_TYPE=Release \
    -DENABLE_HTTP_STREAM_PLAYBACK=ON \
    -DENABLE_KDE=ON

  make
}

package() {
  cd "$srcdir/build"

  make DESTDIR="$pkgdir" PREFIX=`kde4-config --prefix` install
}
