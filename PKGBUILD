# Maintainer: Evgeniy Alekseev <arcanis at archlinux dot org>
# Contributor: Bartłomiej Piotrowski <bpiotrowski at archlinux dot org>
# Contributor: Felipe Hommen <felibank at gmail dot com>
# Contributor: moostik <mooostik at gmail dot com>

pkgname=geogebra
pkgver=6.0.562.0
pkgrel=1
pkgdesc="Dynamic mathematics software with interactive graphics, algebra and spreadsheet"
arch=('x86_64')
url='https://www.geogebra.org/'
license=('GPL3' 'CCPL:by-sa' 'CCPL:by-nc')
depends=('desktop-file-utils' 'electron2' 'shared-mime-info' 'xdg-utils')
makedepends=('gendesk')
source=("https://download.geogebra.org/installers/6.0/GeoGebra-Linux64-Portable-${pkgver//./-}.zip"
        "https://static.geogebra.org/images/geogebra-logo.svg"
        "geogebra"
        "geogebra-mime.xml")
changelog=ChangeLog

prepare() {
  gendesk -f -n --pkgname "${pkgname}" --pkgdesc "${pkgdesc}" \
          --name="GeoGebra" \
          --categories="Education;Science;Math" \
          --mimetypes="application/vnd.geogebra.file;application/vnd.geogebra.tool"
}

package() {
  cd "GeoGebra-linux-x64"

  install -Dm755 "${srcdir}/geogebra" "${pkgdir}/usr/bin/geogebra"
  install -dm755 "${pkgdir}/usr/lib/geogebra"
  cp -dpr --no-preserve=ownership "resources" "${pkgdir}/usr/lib/geogebra"
  cp -dpr --no-preserve=ownership "locales" "${pkgdir}/usr/lib/geogebra"

  install -Dm644 "${srcdir}/geogebra.desktop" "${pkgdir}/usr/share/applications/geogebra.desktop"
  install -Dm644 "${srcdir}/geogebra-logo.svg" "${pkgdir}/usr/share/icons/hicolor/scalable/apps/geogebra.svg"
  install -Dm644 "${srcdir}/geogebra-mime.xml" "${pkgdir}/usr/share/mime/packages/geogebra.xml"
}

md5sums=('bd53237e54f18fc6c045cb48be65d157'
         '863782da033f1a337e688b544afb7d07'
         'ce697901c069ddbe5cfd69cf2d131993'
         '02b66f7d27268b1a446de7d8ab879dc8')
