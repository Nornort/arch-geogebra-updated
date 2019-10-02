# Maintainer: Evgeniy Alekseev <arcanis at archlinux dot org>
# Contributor: Bartłomiej Piotrowski <bpiotrowski at archlinux dot org>
# Contributor: Felipe Hommen <felibank at gmail dot com>
# Contributor: moostik <mooostik at gmail dot com>

pkgname=geogebra
pkgver=6.0.560.0
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

sha512sums=('1252e2c8774933d5a7b4c47f68d2f52e43cde2f2637844db85ebef84e98fd5063e8cb87255091ee1ebe069d2b132a83e39eb0ac74b9352fe5546c1d07a1ac73d'
            'a946acb8867f497c68ce6f8fff8172da4a43a9ca118aafcc5ac414318fd52c4bc6ada387bdfa296f0ff2e1d7411ae345b61197b4adaa3f54299aab837647df55'
            '9fecb6e28acbd99e2761907150ccd119510de544c108fffc1be0bfe84db14d6652f673bd74dd2a67d27416a17dffc22b67577738c21817205b73c8e432ae1d07'
            '415e73ff15524d5e81b05cf4c31241f4e21a4eedcef0a11e5af82423f9a7c2cbf632e9ee1e86b4cc60ebc566472462979a65cb7f3cfc9f94243fb545ac042a0f')
