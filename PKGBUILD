# Maintainer: wifiextender <aaron_caffrey at hotmail dot com>

pkgname=firefox-stable
pkgver=29.0.1
pkgrel=1
pkgdesc="Latest stable firefox x86_64 (en-GB)"
arch=('x86_64')
license=('MPL' 'GPL' 'LGPL')
url="http://www.mozilla.org/en-GB/products/#firefox"
depends=('dbus-glib' 'gtk2' 'lib32-libxt' 'libxt' 'alsa-lib' 'nss' 'lib32-libxcb' 'libxcb')
source=("https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-x86_64/en-GB/firefox-$pkgver.tar.bz2"
        'firefox-stable.desktop' 'package-updater.py')
md5sums=('745ebb3beb28173f6a3d1537859e4c81'
         '96efdc35b753e5547427494402bc2f26'
         '79a7c4be3b9c340cc61cf2ac5bcef6bc')

package() {
  # directory and files
  msg "Building Firefox $pkgver package... "
  cd ${pkgdir}
  mkdir -p {usr/bin,usr/lib}
  cp -r ${srcdir}/firefox usr/lib/${pkgname}
  mv usr/lib/${pkgname}/firefox usr/lib/${pkgname}/firefox-bin
  cat <<EOF > usr/bin/${pkgname}
#!/bin/bash
/usr/lib/${pkgname}/firefox-bin
EOF
  chmod +x usr/bin/${pkgname}

  # desktop icons
  cd ${srcdir}
  install -d ${pkgdir}/usr/share/applications
  install -Dm644 firefox-stable.desktop ${pkgdir}/usr/share/applications
  install -Dm644 firefox/browser/icons/mozicon128.png ${pkgdir}/usr/share/pixmaps/firefox.png
}

