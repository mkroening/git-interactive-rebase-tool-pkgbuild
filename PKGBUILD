# Maintainer: Gabriel Guldner <gabriel at guldner dot eu>
# Contributor: Martin Kröning <m.kroening@hotmail.de>

pkgname=git-interactive-rebase-tool
pkgver=2.0.0
pkgrel=1
pkgdesc='Native cross platform full feature terminal based sequence editor for git interactive rebase. Written in Rust using ncurses.'
arch=('x86_64')
url='https://github.com/MitMaro/git-interactive-rebase-tool'
license=('GPL3')
depends=('rust')
makedepends=('rust' 'cargo')
install=$pkgname.install
source=("$pkgname-$pkgver.tar.gz::https://github.com/MitMaro/$pkgname/archive/$pkgver.tar.gz")
sha256sums=('572815b6bf152cae9414635caf9c8c918a575747c3a8885767380da4aeeeb709')

build() {
  cd "$pkgname-$pkgver"

  cargo build --release --locked --target-dir=target
}

package() {
  cd "$pkgname-$pkgver"

  mkdir -p $pkgdir/usr/bin
  mkdir -p $pkgdir/usr/share/man/man1
  mkdir -p $pkgdir/usr/share/licenses/$pkgname
  install -m755 target/release/interactive-rebase-tool $pkgdir/usr/bin/interactive-rebase-tool
  install -m644 src/interactive-rebase-tool.1 $pkgdir/usr/share/man/man1/interactive-rebase-tool.1
  install -m644 LICENSE $pkgdir/usr/share/licenses/$pkgname
  gzip $pkgdir/usr/share/man/man1/interactive-rebase-tool.1
}

