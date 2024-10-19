# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>

_git=false
_local=false
_py="python"
_py2="${_py}2"
_proj="hip"
_pkg="luks"
pkgname="${_pkg}-tools"
pkgver=0.0.0.0.0.1.1.1
pkgrel=1
_pkgdesc=(
  "A collection of LUKS"
  "related scripts."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_gl="gitlab.com"
_gh="github.com"
_host="https://${_gh}"
_ns='themartiancompany'
_local="${HOME}/${pkgname}"
url="${_host}/${_ns}/${pkgname}"
license=(
  AGPL3
)
depends=(
  'cryptsetup'
  'libcrash-bash'
  'util-linux'
)
makedepends=(
)
[[ "${_git}" == true ]] && \
  makedepends+=(
    git
  )
checkdepends=(
  shellcheck
)
optdepends=(
  "${_py}-pygments: colorized output"
)
groups=(
 "${_proj}"
)
provides=(
  "mk${_pkg}=${pkgver}"
)
_branch="master"
_commit="84fb4c00f9569e4e182dca872563c35c7257d8c6"
source=()
sha256sums=()
[[ "${_git}" == true ]] && \
  if [[ "${_local}" == true ]]; then
    source+=(
      "${pkgname}-${pkgver}::git+${_local}#commit=${_commit}"
    )
  elif [[ "${_local}" == false ]]; then
    source+=(
      "${pkgname}-${pkgver}::git+${url}#commit=${_commit}"
    )
  fi && \
    sha256sums+=(
      SKIP
    )
[[ "${_git}" == false ]] && \
    source+=(
      "${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz"
    ) && \
    sha256sums+=(
      "963b1db06422e211a38563a7f485cfa281262e0b3320273aa35d6abe2e07fc74"
    )
validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
)

check() {
  ls "${srcdir}"
  cd \
    "${pkgname}-${pkgver}"
  make \
    -k \
    check
}

package() {
  cd \
    "${pkgname}-${pkgver}"
  make \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et
