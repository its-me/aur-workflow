# Maintainer: Sergey Kanafyev <sergeykanafyev@gmail.com>
# Automation: https://github.com/its-me/dummy.aur.package

pkgname=package
_pkgname=dummy.releases
pkgver=0.2.2
pkgrel=1
pkgdesc="Dummy package used to exercise the aur-workflow CI/publish pipeline (tracks tagged releases)"
arch=('any')
url="https://github.com/its-me/dummy.releases"
license=('MIT')
source=("${_pkgname}-${pkgver}.tar.gz::https://github.com/its-me/dummy.releases/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('88a61db4817041e9d180adbe20ed78166113f8d15ec17d356f2629efb42cc071')

package() {
    cd "${_pkgname}-${pkgver}"
    install -Dm644 activity.log "${pkgdir}/usr/share/doc/${pkgname}/activity.log"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
