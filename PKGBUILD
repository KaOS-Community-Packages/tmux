pkgname=tmux
pkgver=2.6
pkgrel=1
pkgdesc='A terminal multiplexer'
url='http://tmux.github.io/'
arch=('x86_64')
license=('BSD/ISC')
depends=('ncurses' 'libevent')
source=("https://github.com/$pkgname/$pkgname/releases/download/$pkgver/$pkgname-$pkgver.tar.gz" "tmux"  "tmux.vim")
sha256sums=('b17cd170a94d7b58c0698752e1f4f263ab6dc47425230df7e53a6435cc7cd7e8'
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
