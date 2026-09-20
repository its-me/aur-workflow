# Maintainer: Sergey Kanafyev <sergeykanafyev@gmail.com>
# Automation: https://github.com/its-me/dummy.aur.package

pkgname=package
_pkgname=dummy.releases
pkgver=0.2.3
pkgrel=1
pkgdesc="Dummy package used to exercise the aur-workflow CI/publish pipeline (tracks tagged releases)"
arch=('any')
url="https://github.com/its-me/dummy.releases"
license=('MIT')
source=("${_pkgname}-${pkgver}.tar.gz::https://github.com/its-me/dummy.releases/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('ef3765ab822f877fc834e1ac7ebca07a6b15fb96fa62994f0af7b0ba1f5e686c')

package() {
    cd "${_pkgname}-${pkgver}"
    install -Dm644 activity.log "${pkgdir}/usr/share/doc/${pkgname}/activity.log"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
