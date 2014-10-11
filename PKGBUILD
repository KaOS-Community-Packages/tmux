# $Id: PKGBUILD 106145 2014-02-24 08:39:29Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer:  TDY <tdy@gmx.com>
# Contributor: Grigorios Bouzakis <grbzks[at]gmail[dot]com>

pkgname=tmux
pkgver=1.9_a
pkgrel=1
pkgdesc='A terminal multiplexer'
url='http://tmux.sourceforge.net/'
arch=('i686' 'x86_64')
license=('BSD')
depends=('ncurses' 'libevent')
source=(http://downloads.sourceforge.net/tmux/tmux-${pkgver/_/}.tar.gz
		LICENSE)
md5sums=('b07601711f96f1d260b390513b509a2d'
         '71601bc37fa44e4395580b321963018e')

build() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	make install DESTDIR=$pkgdir
	install -Dm644 ../LICENSE "$pkgdir/usr/share/licenses/tmux/LICENSE"

	install -dm755 "$pkgdir/usr/share/tmux/"
	install -m644 examples/* "$pkgdir/usr/share/tmux/"
	install -Dm644 examples/tmux.vim "$pkgdir/usr/share/vim/vimfiles/syntax/tmux.vim"

	install -d $pkgdir/usr/share/bash-completion/completions/
	mv $pkgdir/usr/share/tmux/bash_completion_tmux.sh $pkgdir/usr/share/bash-completion/completions/tmux
}
