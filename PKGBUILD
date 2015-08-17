# Maintainer: Xiao-Long Chen <chenxiaolong@cxl.epac.to>

pkgname=wxhexeditor-updated
pkgver=0.20
pkgrel=1
pkgdesc="a free hex editor / disk editor for Linux, Windows and MacOSX"
arch=('i686' 'x86_64')
url="http://wxhexeditor.sourceforge.net/"
license=('GPL')
depends=('udis86' 'wxgtk')
provides=("wxhexeditor=${pkgver}")
conflicts=('wxhexeditor')
source=("http://downloads.sourceforge.net/project/wxhexeditor/wxHexEditor/v${pkgver}%20Beta/wxHexEditor-v${pkgver}-src.tar.bz2"
        'use_shared_udis86.patch'
        'mhash_fix.patch'
        'makefile_prefix.patch')
sha512sums=('f8138fb892528fd7d131b0931f52cb6b19dc984aa831882d7f60f557527e6bb559429a11b5a1307cf51d1a8974123627d15ccee87561970784a75910929f85a3'
            'a95d650f942a50e5e04b834bce79d4bc9153daa8b0be737564b2842e9bd54e55c9023df15ce314d37c0ddd11d3e2ae8f13af5c1d857efd5b753e6f4ae194982d'
            '78bd318af3cfcc72c29f4e89593ac6d3f2ee6da58ba79719e6926feb0eaabae266697e1ee93ad221bde169fbaa55e03a910ceeb16d9ff9562fb186ff38706668'
            'c399243659888707fed3def20032ab4958ffcdd99492258891e7445f8c50e3c183d768d2297ac6a4e757d37add4c27a9c7481d6edd414f44a506060d4a984bcc')

build() {
  cd "${srcdir}/wxHexEditor"

  # Use shared libraries
  #rm -rvf udis86 mhash
  patch -Np1 -i "${srcdir}/use_shared_udis86.patch"
  patch -Np1 -i "${srcdir}/mhash_fix.patch"

  #CXXFLAGS="${CXXFLAGS} -fpermissive"
  MAKEFLAGS="-j1"
  make ${MAKEFLAGS}
}

check() {
  cd "${srcdir}/wxHexEditor"
  msg "Nothing to check."
}

package() {
  cd "${srcdir}/wxHexEditor"
  make PREFIX="${pkgdir}/usr/" install
}

# vim:set ts=2 sw=2 et:
