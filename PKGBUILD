# Maintainer: schuay <jakob.gruber@gmail.com>

pkgname=eiffelstudio
pkgver=14.05
pkgrel=2
pkgdesc='Opensource edition of EiffeStudio, an IDE for Eiffel language'
arch=('i686' 'x86_64')
url='http://www.eiffel.com/eiffelstudio/'
license=('GPL')
depends=('gtk2' 'libxtst')
options=('staticlibs')

source=('http://downloads.sourceforge.net/project/eiffelstudio/EiffelStudio%2014.05/Build_95417/Eiffel_14.05_gpl_95417-linux-x86-64.tar.bz2')
_platform="linux-x86-64"
md5sums=('5b8a9509d7ff010db7d9028d644ad7e8')

if [ "$CARCH" == "i686" ]; then
    source=('http://downloads.sourceforge.net/project/eiffelstudio/EiffelStudio%2014.05/Build_95417/Eiffel_14.05_gpl_95417-linux-x86.tar.bz2')
    _platform="linux-x86"
    md5sums=('4c50d24e57dcb5c899c78232e1e5bc71')
fi

package() {
    mkdir -p "${pkgdir}/opt"
    mv "${srcdir}/Eiffel_14.05" "${pkgdir}/opt/"

    mkdir -p "${pkgdir}/usr/bin"
    echo "#!/bin/bash" >> "${pkgdir}/usr/bin/eiffelstudio"
    echo "export ISE_EIFFEL=/opt/Eiffel_14.05" >> "${pkgdir}/usr/bin/eiffelstudio"
    echo "export ISE_PLATFORM=${_platform}" >> "${pkgdir}/usr/bin/eiffelstudio"
    echo "export PATH=\"$PATH:\${ISE_EIFFEL}/studio/spec/\${ISE_PLATFORM}/bin\"" >> "${pkgdir}/usr/bin/eiffelstudio"
    echo "estudio $@" >> "${pkgdir}/usr/bin/eiffelstudio"
    chmod 755 "${pkgdir}/usr/bin/eiffelstudio"
}

