# PKGBUILD
pkgname=ironhibit-idle-socket
pkgver=1.0.0
pkgrel=1
pkgdesc="User systemd ironhibit service with transient timer and UNIX socket for time-remaining queries"
arch=('any')
url='https://example.invalid'
license=('MIT')
depends=('systemd')
source=('ironhibit@.service' 'ironhibit.socket')
sha256sums=('SKIP' 'SKIP')

package() {
  install -Dm644 "$srcdir/ironhibit@.service" "$pkgdir/usr/lib/systemd/user/ironhibit@.service"
  install -Dm644 "$srcdir/ironhibit.socket"    "$pkgdir/usr/lib/systemd/user/ironhibit.socket"
  install -dm755 "$pkgdir/usr/share/licenses/$pkgname"
  printf '%s\n' "MIT (units only)" > "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

