#
# This is the PKGBUILD for Linux System Performance and Status Monitor Package
#

pkgname=system_monitor
pkgver=1.1.0
pkgrel=1
pkgdesc="Publish System Performance and Status Data to MQTT"
arch=('i686' 'x86_64' 'arm' 'armv6h' 'armv7h')
url="http://happy-lab.llc/"
depends=('python3')
provides=('system_monitor')
license=('MIT')
source=("$pkgname" "$pkgname.service" "$pkgname.conf.example" "LICENSE")
install=$pkgname.install
sha256sums=('967e5de02b3b2c3927e0076bc7a913baad6a7072088abce5389d2c881b86a8d9'
            '11cc7fb71f5e5ffaa72c284bb9c3bdf5e8db72e467264b9a63f27dd8f0cfb20c'
            '50ed716fb901fed1a1a36425da0c92c42cec6262762f9ccf935ff5a4f75072e6'
	    '847c12d8681bb838663288a5260242f96c6b36666f234ddc163b8fc294619e4c')

package() {

  # Daemon
  install -Dm755 "$pkgname" "$pkgdir/usr/bin/$pkgname"

  # Daemon systemd service file
  install -Dm644 "$pkgname.service" "$pkgdir/usr/lib/systemd/system/$pkgname.service"

  # Daemon configuration file
  install -Dm644 "$pkgname.conf.example" "$pkgdir/etc/sensors/$pkgname.conf.example"

  # Daemon PID file
  #echo 'pid_file /run/$pkgname.pid' >> "$pkgdir/etc/sensors/$pkgname.conf.example"

  # License
  install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

}
