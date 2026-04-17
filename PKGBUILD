# Maintainer: acidtracks
pkgname=ultimate-gaming-server
pkgver=1.0.0
pkgrel=1
pkgdesc="Sunshine game streaming + wake-on-LAN setup pour Hyprland/Wayland (moniteur virtuel, watchdog, bascule écran)"
arch=('any')
license=('MIT')
depends=(
  'python>=3.11'
  'sunshine-beta-bin'
  'hyprland'
  'iproute2'
)
optdepends=(
  'ethtool: activation du Wake-on-LAN sur la carte réseau'
)
install=$pkgname.install
sha256sums=()

package() {
  cd "$startdir"

  local _bindir="$pkgdir/usr/bin"
  local _systemd="$pkgdir/usr/lib/systemd/user"

  # Scripts
  install -Dm755 scripts/start-sunshine            "$_bindir/start-sunshine"
  install -Dm755 scripts/switch-display            "$_bindir/switch-display"
  install -Dm755 scripts/sunshine-watchdog         "$_bindir/sunshine-watchdog"
  install -Dm755 scripts/sunshine-trigger          "$_bindir/sunshine-trigger"

  # Units systemd utilisateur
  install -Dm644 systemd/sunshine.service          "$_systemd/sunshine.service"
  install -Dm644 systemd/sunshine.socket           "$_systemd/sunshine.socket"
  install -Dm644 systemd/sunshine-watchdog.service "$_systemd/sunshine-watchdog.service"

}
