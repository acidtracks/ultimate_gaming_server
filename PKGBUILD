# Maintainer: acidtracks <julien.huchet44@gmail.com>
pkgname=ultimate-gaming-server
pkgver=0.1.0
pkgrel=1
pkgdesc="Sunshine socket-activated streaming server with virtual X11 display"
arch=('any')
url="https://github.com/acidtracks/ultimate_gaming_server"
license=('MIT')
depends=('sunshine' 'xorg-xinit' 'openbox' 'xorg-xrandr' 'bc' 'sudo')
install=ultimate-gaming-server.install
backup=(
    "etc/ultimate_gaming_server/ugs.conf"
    "etc/sudoers.d/ultimate_gaming_server"
)
source=("git+https://github.com/acidtracks/ultimate_gaming_server.git")
sha256sums=('SKIP')

package() {
    cd "$srcdir/ultimate_gaming_server"

    # Scripts
    install -Dm755 scripts/vt-save-switch      "$pkgdir/usr/bin/vt-save-switch"
    install -Dm755 scripts/vt-restore          "$pkgdir/usr/bin/vt-restore"
    install -Dm755 scripts/sunshine-watchdog   "$pkgdir/usr/bin/sunshine-watchdog"
    install -Dm755 scripts/ugs-virtual-display         "$pkgdir/usr/bin/ugs-virtual-display"
    install -Dm755 scripts/ugs-virtual-display-manager "$pkgdir/usr/bin/ugs-virtual-display-manager"
    install -Dm755 scripts/sunshine-hooks              "$pkgdir/usr/bin/sunshine-hooks"

    # Configuration
    install -Dm644 conf/ugs.conf \
        "$pkgdir/etc/ultimate_gaming_server/ugs.conf"
    install -Dm644 conf/ugs-xserver.conf \
        "$pkgdir/etc/X11/ultimate_gaming_server/ugs-xserver.conf"

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
