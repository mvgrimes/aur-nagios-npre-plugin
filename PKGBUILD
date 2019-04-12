# Maintainer: Mark Grimes <mgrimes at peculier dot com>
# Contributor: Idares <idares@seznam.cz>
# https://github.com/mvgrimes/aur-nagios-npre-plugin

pkgname=nagios-nrpe-plugin
pkgver=3.2.1
pkgrel=2
pkgdesc="The Nagios Server NRPE plugin (install on the monitoring machine)."
license=('GPL')
arch=('any')
url="http://www.nagios.org"
source=("http://downloads.sourceforge.net/nagios/nrpe-${pkgver}.tar.gz")
md5sums=('8997e195fea93cdceb8c7ed8ac1d43bc')
depends=(nagios)
install=nagios-nrpe-plugin.install

# nagios already depends on openssl-1.0

build() {
    cd ${srcdir}/nrpe-${pkgver}
    ./configure \
        --prefix=/usr/share/nagios \
        --enable-ssl \
        --with-nagios-user=nagios \
        --with-nagios-group=nagios \
            || return 1
    make nrpe || return 1
}

package() {
    cd ${srcdir}/nrpe-${pkgver}
    make DESTDIR=${pkgdir} install-plugin || return 1
}
