# Maintainer: Gabriel Guldner <gabriel at guldner dot eu>
# Contributor: Martin Kröning <m.kroening@hotmail.de>

pkgname=git-interactive-rebase-tool
_binname=interactive-rebase-tool
pkgver=2.0.0
pkgrel=1
pkgdesc='Native cross-platform full feature terminal-based sequence editor for git interactive rebase.'
arch=('x86_64')
url='https://gitrebasetool.mitmaro.ca/'
license=('GPL3')
depends=('gcc-libs' 'zlib')
makedepends=('cargo')
install=$pkgname.install
source=("$pkgname-$pkgver.tar.gz::https://github.com/MitMaro/$pkgname/archive/$pkgver.tar.gz")
sha256sums=('572815b6bf152cae9414635caf9c8c918a575747c3a8885767380da4aeeeb709')

build() {
  cd "$pkgname-$pkgver"

  cargo build --release --locked --target-dir=target
}

check() {
  cd "$pkgname-$pkgver"

  cargo test --release --locked --target-dir=target
}

package() {
  cd "$pkgname-$pkgver"

  install -Dm 755 target/release/$_binname -t "$pkgdir/usr/bin"
  install -Dm 644 src/$_binname.1 -t "$pkgdir/usr/share/man/man1"
}
