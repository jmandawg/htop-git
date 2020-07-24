# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: Angel Velasquez <angvp@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=htop
pkgver=2.2.0
pkgrel=3
pkgdesc='Interactive process viewer'
arch=('x86_64')
url='https://hisham.hm/htop/'
license=('GPL')
depends=('ncurses' 'libnl')
makedepends=('python')
optdepends=('lsof: show files opened by a process'
            'strace: attach to a running process')
options=('!emptydirs' debug)
validpgpkeys=('8460980B2B79786DE0C7FCC83FD8F43C2BB3C478') # Hisham Muhammad <h@hisham.hm>
source=("$pkgname-$pkgver.tar.gz"
        '0001-fix-option-string.patch'
        '0002-gcc10.patch')

prepare() {
  cd "$pkgname-$pkgver"

  patch -Np1 < "${srcdir}"/0001-fix-option-string.patch
  patch -Np1 < "${srcdir}"/0002-gcc10.patch
}

build() {
  cd "$pkgname-$pkgver"

  ./configure \
      --prefix=/usr \
      --sysconfdir=/etc \
      --enable-cgroup \
      --enable-delayacct \
      --enable-openvz \
      --enable-unicode \
      --enable-vserver

  make
}

package() {
  make -C "$pkgname-$pkgver" DESTDIR="$pkgdir" install
}
