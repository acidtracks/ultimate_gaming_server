# Maintainer: acidtracks <julien.huchet44@gmail.com>
pkgname=ultimate-gaming-server
pkgver=0.1.0
pkgrel=1
pkgdesc="Sunshine socket-activated streaming server with headless X11 on VT8"
arch=('any')
url="https://github.com/acidtracks/ultimate_gaming_server"
license=('MIT')
depends=('sunshine' 'xorg-xinit' 'openbox' 'sudo')
install=ultimate-gaming-server.install
backup=("etc/sudoers.d/ultimate_gaming_server")
source=("git+https://github.com/acidtracks/ultimate_gaming_server.git")
sha256sums=('SKIP')

package() {
    cd "$srcdir/ultimate_gaming_server"

    # Scripts
    install -Dm755 scripts/vt-save-switch   "$pkgdir/usr/bin/vt-save-switch"
    install -Dm755 scripts/vt-restore       "$pkgdir/usr/bin/vt-restore"
    install -Dm755 scripts/sunshine-watchdog "$pkgdir/usr/bin/sunshine-watchdog"

    # System unit
    install -Dm644 systemd/ugs-xserver.service \
        "$pkgdir/usr/lib/systemd/system/ugs-xserver.service"

    # User units
    install -Dm644 systemd/ugs.service \
        "$pkgdir/usr/lib/systemd/user/ugs.service"
    install -Dm644 systemd/ugs.socket \
        "$pkgdir/usr/lib/systemd/user/ugs.socket"
    install -Dm644 systemd/ugs-watchdog.service \
        "$pkgdir/usr/lib/systemd/user/ugs-watchdog.service"

    # Sudoers
    install -Dm440 sudoers/ultimate_gaming_server \
        "$pkgdir/etc/sudoers.d/ultimate_gaming_server"
}
