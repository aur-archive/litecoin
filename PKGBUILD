## Maintainer : gee
## based of shahid's bitcoin pkgbuild

#For the first few weeks of 0.8.6.1
#edit litecoin.conf (or create a new file) adding the following example information:
#addnode=<address>
#Replace <address> with one of the addresses listed in this file: https://litecoin.org/downloads/SUPERNODES.txt

pkgname=litecoin
pkgver=0.8.7.4
pkgrel=12
pkgdesc="Litecoin is a peer-to-peer network based digital currency."
arch=('i686' 'x86_64')
url="http://www.litecoin.org/"
depends=('qt4' 'libpng' 'expat' 'gcc-libs' 'boost-libs' 'openssl')
makedepends=('boost' 'gcc' 'make' 'automoc4')
optdepends=('cpuminer')
license=('MIT')
source=("https://github.com/${pkgname}-project/${pkgname}/archive/v${pkgver}.tar.gz"
	"${pkgname}.desktop")

makefile_unix=makefile.unix
makefile_qt=Makefile
build() {
        cd ${pkgname}-${pkgver}/src

	make USE_UPNP=- -f $makefile_unix litecoind

	cd ..
	qmake-qt4 "USE_UPNP=-"	
	make USE_UPNP=-
}


package() {
	mkdir -p $pkgdir/usr/bin
	mkdir -p $pkgdir/usr/share/pixmaps
	mkdir -p $pkgdir/usr/share/applications
	
	install -D -m755 ${pkgname}-${pkgver}/litecoin-qt $pkgdir/usr/bin/
	install -D -m755 ${pkgname}-${pkgver}/src/litecoind $pkgdir/usr/bin/	
	install -D -m644 ${pkgname}-${pkgver}/src/qt/res/icons/bitcoin.png $pkgdir/usr/share/pixmaps/${pkgname}.png
	install -D -m644 $srcdir/${pkgname}.desktop $pkgdir/usr/share/applications/ 
}
md5sums=('00f78ec32cf69ec7e05e8841e9e5f94a'
         'bd748637de374ec28dbfb201b42d0116')
