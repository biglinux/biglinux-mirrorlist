# Maintainer: Bruno Gonçalves <bigbruno@gmail.com>
# Maintainer: Tales A. Mendonça <talesam@gmail.com>

pkgname=biglinux-mirrorlist
pkgdesc="BigLinux repository mirrorlists for pacman"
depends=('pacman')
pkgver=$(date +%y.%m.%d)
pkgrel=$(date +%H%M)
arch=('any')
license=('MIT')
url="https://github.com/biglinux/${pkgname}"
source=("git+${url}.git")
sha256sums=('SKIP')
backup=('etc/pacman.d/biglinux-priority-mirrorlist'
        'etc/pacman.d/biglinux-testing-mirrorlist'
        'etc/pacman.d/biglinux-stable-mirrorlist'
        'etc/pacman.d/biglinux-extra-mirrorlist')

package() {
  cd "${srcdir}/${pkgname}"
  local repo
  for repo in priority testing stable extra; do
    install -Dm644 "biglinux-${repo}-mirrorlist" "${pkgdir}/etc/pacman.d/biglinux-${repo}-mirrorlist"
  done
}
