# Maintainer: wilson <bugs@pandorica.net>
# Contributor: Sebastian Lenz <sebastian@archusers.de>
pkgname=gnome-shell-extension-alternate-tab-git
pkgver=20120814
pkgrel=1
pkgdesc="A replacement for Alt-Tab, allows to cycle between windows and does not group by application."
arch=(any)
url="http://live.gnome.org/GnomeShell/Extensions"
license=('GPL' 'LGPL')
depends=('gnome-shell' 'gnome-shell-extension-common-git')
makedepends=('git' 'gnome-common' 'intltool' 'gettext')
conflicts=('gnome-shell-extension-alternate-tab')
provides=('gnome-shell-extension-alternate-tab')
install='gschemas.install'

_gitroot="git://git.gnome.org/gnome-shell-extensions"
_gitname="alternate-tab"

build() {
  cd "${srcdir}"
  msg "Connecting to GIT server...."
  if [ -d ${_gitname} ] ; then
    cd ${_gitname} && git pull origin
    msg "The local files are updated."
  else
    git clone -b gnome-3-4 ${_gitroot}
    cd gnome-shell-extensions
  fi
  msg "GIT checkout done or server timeout"
  msg "Starting make..."
  cd ${srcdir}/gnome-shell-extensions
  ./autogen.sh --prefix=/usr --enable-extensions="alternate-tab"
}

package() {
  cd ${srcdir}/gnome-shell-extensions
  make DESTDIR=${pkgdir} install
  rm -r ${pkgdir}/usr/share/locale
}

# vim:set ts=2 sw=2 et:
