# Maintainer: Sergey Kanafyev <sergeykanafyev@gmail.com>
# Automation: https://github.com/its-me/dummy.aur.package

pkgname=package
_pkgname=dummy.releases
pkgver=0.2.0
pkgrel=1
pkgdesc="Dummy package used to exercise the aur-workflow CI/publish pipeline (tracks tagged releases)"
arch=('any')
url="https://github.com/its-me/dummy.releases"
license=('MIT')
source=("${_pkgname}-${pkgver}.tar.gz::https://github.com/its-me/dummy.releases/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('e23f66b7f6f4564f645804d2fe8444b43d8c909ddde7e6bab38ca384069718ea')

package() {
    cd "${_pkgname}-${pkgver}"
    install -Dm644 activity.log "${pkgdir}/usr/share/doc/${pkgname}/activity.log"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
