# Maintainer: Sergey Kanafyev <sergeykanafyev@gmail.com>
# Automation: https://github.com/its-me/dummy.aur.package

pkgname=package
_pkgname=dummy.releases
pkgver=0.4.2
pkgrel=1
pkgdesc="Dummy package used to exercise the aur-workflow CI/publish pipeline (tracks tagged releases)"
arch=('any')
url="https://github.com/its-me/dummy.releases"
license=('MIT')
source=("${_pkgname}-${pkgver}.tar.gz::https://github.com/its-me/dummy.releases/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('be5589cb20fb11ae12c064e4d586645233b8d410fa01d4a9de6ba2ab36ff6e9a')

package() {
    cd "${_pkgname}-${pkgver}"
    install -Dm644 activity.log "${pkgdir}/usr/share/doc/${pkgname}/activity.log"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
