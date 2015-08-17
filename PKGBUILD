# $Id$
# Maintainer: Dongsheng Cai <imdongsheng@gmail.com>

pkgname=phppgadmin-git
pkgver=5.1dev
pkgrel=1
pkgdesc="A web-based administration tool for PostgreSQL."
arch=('any')
url="http://sourceforge.net/projects/phppgadmin"
license=('GPL')
depends=('php' 'php-pgsql' 'git')
conflicts=('phppgadmin')
backup=('etc/webapps/phppgadmin/config.inc.php'
	'etc/webapps/phppgadmin/.htaccess')

_gitname="phppgadmin"

build() {
    cd ${srcdir}
    if [ -d $_gitname ]; then
        cd $_gitname
        msg "Updating local files from Git"
        git pull . master
    else
        msg "Cloning Git repository"
        git clone git://github.com/phppgadmin/phppgadmin.git
    fi
    _instdir=$pkgdir/usr/share/webapps/phppgadmin
    mkdir -p ${_instdir} $pkgdir/etc/webapps/phppgadmin
    cd ${_instdir}
    cp -ra $srcdir/${_gitname}/* .
    cp ./conf/config.inc.php-dist $pkgdir/etc/webapps/phppgadmin/config.inc.php
    rm -f ${_instdir}/conf/config.inc.php
    ln -s /etc/webapps/phppgadmin/config.inc.php ${_instdir}/conf/config.inc.php
}
