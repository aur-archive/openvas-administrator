pkgname=openvas-administrator
pkgver=1.3.2
pkgrel=1
groups=('blackarch' 'blackarch-scanner')
pkgdesc="OpenVAS scanner administration tool"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url="http://www.openvas.org/"
license=('GPL')
depends=('glib2' 'openvas-libraries' 'cmake' 'doxygen' 'xmltoman')
options=('!makeflags' '!buildflags')
# The file downloaded is determined by the `/1319/` part. Changing `pkgver`
#  does not change the file downloaded so we hard code the version number to
#  avoid confusion.
source=('http://wald.intevation.org/frs/download.php/1442/openvas-administrator-1.3.2.tar.gz')
md5sums=('0410287e899f6b57c8674c0fe7b6fb1b')

prepare() {
  cd "$srcdir/openvas-administrator-$pkgver"

  find . -name 'CMakeLists.txt' -exec sed -i 's/-Werror//' {} \;
}

build() {
  cd "$srcdir/openvas-administrator-$pkgver"

  cmake -DCMAKE_INSTALL_PREFIX=/usr -DSYSCONFDIR=/etc -DLOCALSTATEDIR=/var -DSBINDIR=/usr/bin .
  make
}

package() {
  cd "$srcdir/openvas-administrator-$pkgver"

  make DESTDIR="$pkgdir/" install
}
