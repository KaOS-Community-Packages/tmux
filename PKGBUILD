pkgname=tmux
pkgver=2.5
pkgrel=1
pkgdesc='A terminal multiplexer'
url='http://tmux.github.io/'
arch=('x86_64')
license=('BSD')
depends=('ncurses' 'libevent' 'libutempter')
source=(https://github.com/tmux/tmux/releases/download/$pkgver/tmux-$pkgver.tar.gz
	LICENSE)
sha256sums=('ae135ec37c1bf6b7750a84e3a35e93d91033a806943e034521c8af51b12d95df'
            'b5de80619e4884ced2dfe0a96020e85dcfb715a831ecdfdd7ce8c97b5a6ff2cc')

build() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	make install DESTDIR="$pkgdir"
	install -Dm644 "$srcdir"/LICENSE "$pkgdir/usr/share/licenses/tmux/LICENSE"
}
