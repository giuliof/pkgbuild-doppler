pkgname=doppler-git
pkgver=20180827
pkgrel=1
pkgdesc="Command line utility that takes IQ data stream as input and produces doppler corrected output stream based on TLE."
arch=('i686' 'x86_64')
url="https://github.com/cubehub/doppler"
license=('MIT')
depends=('libgpredict' 'liquid-dsp')
makedepends=('rust')
#_gitroot=https://github.com/phirsch/gqrx
#_gitroot=https://github.com/mathisschmieder/gqrx
_gitroot=git://github.com/cubehub/doppler.git
_gitname=doppler
source=("$_gitname::$_gitroot")
md5sums=('SKIP')
sha256sums=('SKIP')

pkgver() {
  cd "$_gitname"
  # disable $HOME to prevent git to use user's configuration
  HOME=/dev/null git log -1 --format="%cd" --date=short | tr -d '-'
}

build() {
	cd "$_gitname"
	cargo build --release
}

package() {
	cd "$_gitname"
  	install -D -m755 target/release/doppler $pkgdir/usr/local/bin/doppler
}

# Install order: rtl-sdr-git, libuhd, gnuradio-git, gr-osmosdr-git, gqrx-git

