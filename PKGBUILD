pkgname=tmux
pkgver=2.5
pkgrel=1
pkgdesc='A terminal multiplexer'
url='http://tmux.github.io/'
arch=('x86_64')
license=('BSD/ISC')
depends=('ncurses' 'libevent')
source=("https://github.com/$pkgname/$pkgname/releases/download/$pkgver/$pkgname-$pkgver.tar.gz" "tmux"  "tmux.vim")
sha256sums=('ae135ec37c1bf6b7750a84e3a35e93d91033a806943e034521c8af51b12d95df'
	    'ddc39f954970e9c6a5d882a8f9ffe299e538573fa38a0b85ba564e02be77537a'
	    '4355342d73afcb7776b60ba5dbd7e9abb267d370a5c07e58c25cb4731f7d00c7')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make install DESTDIR=$pkgdir
	install -Dm644  COPYING "$pkgdir/usr/share/licenses/tmux/LICENSE"

	install -Dm644 example_tmux.conf "$pkgdir/usr/share/tmux/example_tmux.conf"
	install -Dm644 ../tmux.vim "$pkgdir/usr/share/vim/vimfiles/syntax/tmux.vim"

	install -Dm644 ../tmux "$pkgdir/usr/share/bash-completion/completions/tmux"
}
