# Contributor: Balló György <ballogyor+arch at gmail dot com>

pkgname=gwibber-devel
_pkgname=gwibber
pkgver=3.4.1
pkgrel=1
pkgdesc="Microblogging client for GNOME, which supports Twitter, Identi.ca, StatusNet, Facebook, Flickr, Digg, FriendFeed and Qaiku"
arch=('i686' 'x86_64')
url="http://gwibber.com/"
license=('GPL')
depends=('libgee' 'libnotify' 'dee>=1.0.0' 'json-glib' 'gtkspell3' 'python2-gobject' 'libwnck3' 'libwebkit3' 'libgnome-keyring>=3.3' 'dbus-python' 'python2-httplib2' 'python-egenix-mx-base' 'python2-oauth' 'python-imaging' 'pyxdg' 'dconf' 'hicolor-icon-theme' 'xdg-utils')
makedepends=('intltool' 'vala>=0.15.0')
provides=('gwibber')
conflicts=('gwibber')
options=('!libtool')
install=$_pkgname.install
source=(http://launchpad.net/$_pkgname/${pkgver%.*}/$pkgver/+download/$_pkgname-$pkgver.tar.gz)
md5sums=('47d27eaa1fe1c94a959acff7128a644a')

build() {
  cd "$srcdir/$_pkgname-$pkgver"
  find . -type f | xargs sed -i 's@^#!.*python$@#!/usr/bin/python2@'

  ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
              --disable-static --disable-schemas-compile --disable-unity
  make
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"

  make DESTDIR="$pkgdir" install
}
