#Maintainer: Jonas Strassel <jo.strassel@gmail.com>
pkgname=glimmer
pkgver=0.0.4
pkgrel=1
pkgdesc="A small tool to use along with i3/Sway to add CSS-powered decorations to your focused windows, for better usability."
arch=('x86_64' 'aarch64')
url="https://github.com/moustacheful/glimmer.git"
license=('MIT')
depends=()
makedepends=('cargo' 'pango' 'gdk-pixbuf2' 'atkmm' 'gtk3')
source=("$pkgname-$pkgver.tar.gz::https://static.crates.io/crates/$pkgname/$pkgname-$pkgver.crate")

sha256sums=('72882ef12f3c39a4352db5ff4ccf9fd6ca9f51d44d22a30422ff51c8838789f7')

build() {
   cd $pkgname-$pkgver
   RUSTUP_TOOLCHAIN=stable cargo build --release --locked --all-features --target-dir=target
}

check() {
   cd $pkgname-$pkgver
   RUSTUP_TOOLCHAIN=stable HOME=$(pwd) cargo test --release --locked --target-dir=target
}

package() {
   cd $pkgname-$pkgver
   install -Dm755 "target/release/glimmer" "$pkgdir/usr/bin/glimmer"
}
