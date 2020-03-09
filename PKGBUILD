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
source=('system_monitord' 'system_monitor.service' 'system_monitor.conf.example' 'LICENSE')
install=$pkgname.install
sha256sums=('b2dfc979a4e2db534006820099970032b601851b056346b91845e7c5d45a1892'
            'd3a82f3dd628f041ffb36f8bdb86de981ed570861a9885fd85167e84480d93c4'
            '50ed716fb901fed1a1a36425da0c92c42cec6262762f9ccf935ff5a4f75072e6'
	    '847c12d8681bb838663288a5260242f96c6b36666f234ddc163b8fc294619e4c')

package() {

  # Daemon
  install -Dm755 "system_monitord" "${pkgdir}/usr/bin/system_monitord"

  # Daemon systemd service file
  install -Dm644 "system_monitor.service" "${pkgdir}/usr/lib/systemd/system/system_monitor.service"

  # Daemon configuration file
  install -Dm644 "system_monitor.conf.example" "${pkgdir}/etc/sensors/system_monitor.conf.example"

  # Daemon PID file
  #echo 'pid_file /run/system_monitor.pid' >> "${pkgdir}/etc/sensors/system_monitor.conf.example"

  # License
  install -Dm644 "LICENSE" "${pkgdir}/usr/share/licenses/system_monitor/LICENSE"

}
