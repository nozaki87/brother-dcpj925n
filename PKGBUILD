# Contributor: Noz ack <noz.ack44643 at hotmail.com>
#              PKGBUILD adapted from DCP9010cn by Pavel Benak
pkgname=brother-dcpj925n
pkgver=3.0.0
pkgrel=1
pkgdesc="Brother cups and lpd driver for DCP-J925N"
arch=('i686' 'x86_64')
url="http://solutions.brother.com/linux/en_us/index.html"
license=('GPL2' 'custom:Brother Industries')

if [ "$(uname -m)" = "x86_64" ]
then
 depends=('cups' 'lib32-glibc' 'psutils')
else
 depends=('cups' 'psutils')
fi

lprver=3.0.1
install=brother-dcpj925n.install
source=("http://download.brother.com/welcome/dlf100572/dcpj925ncupswrapper-$pkgver-$pkgrel.i386.deb"
	"http://download.brother.com/welcome/dlf100570/dcpj925nlpr-$lprver-$pkgrel.i386.deb"
)

md5sums=('b4d8cff29212d4d22f70e01d91e5a423'
         '8f8e16759578a93d128fe1ac063fe1a9'
)

prepare()
{
 mkdir -p $srcdir/unpack || return 1
 for i in $srcdir/*.deb
 do
  cd $srcdir/unpack
  ar -x $i || return 1
  cd $srcdir
  bsdtar -pxf $srcdir/unpack/data.tar.gz || return 1
 done
}

package()
{
 cp -a $srcdir/opt $pkgdir
 cp -a $srcdir/usr $pkgdir
}
