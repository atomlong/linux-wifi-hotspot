# Maintainer: Dimitris Kiziridis <ragouel at outlook dot com>
# Co-Maintainer: Mark Wagie <mark dot wagie at tutanota dot com>
pkgname=linux-wifi-hotspot
pkgver=3.0.0
pkgrel=1
pkgdesc="Create virtual wifi hotspot using same wifi card which is connected to an AP + many features (a GUI tool)"
arch=('x86_64')
url="https://github.com/lakinduakash/linux-wifi-hotspot"
license=('BSD')
depends=('hostapd'
         'iw'
         'gtk3'
         'procps-ng'
         'dnsmasq'
         'iproute2')
makedepends=('git' 'glade')
optdepends=('haveged: For random MAC generation'
            'wireless_tools: if iw cannot recognize your adapter'
            'bash-completion: for bash completions')
provides=('wihotspot')
conflicts=('wihotspot' 'create_ap')
backup=('etc/create_ap.conf')
install="$pkgname.install"
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz")
sha256sums=('33a24587a27b500e280da8a3d0a32008ed4b54705e021b7284d6649dfbbbf638')

build() {
  cd "${pkgname}-${pkgver}"
  make
}

package() {
  cd "${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install

  install -Dm644 LICENSE -t \
   "${pkgdir}/usr/share/licenses/${pkgname}"
  install -Dm644 src/desktop/hotspot.png \
    "$pkgdir/usr/share/pixmaps/wihotspot.png"
}
# vim:set ts=2 sw=2 et:
