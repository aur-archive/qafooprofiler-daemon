# Maintainer: Benjamin Cremer <bc@benjamin-cremer.de>
# https://github.com/bcremer/pkgbuild/tree/master/qafooprofiler-daemon

pkgname=qafooprofiler-daemon
pkgver=0.3.3
pkgrel=1
pkgdesc="Qafoo Profiler Daemon (qprofd) (unofficial)"
arch=('i686' 'x86_64')
url="http://qafoolabs.com"
license=('custom')
install=qprofd.install

if [[ $CARCH == "x86_64" ]]; then
    source=("https://s3-eu-west-1.amazonaws.com/qafoo-profiler/downloads/qprofd_amd64-$pkgver.tar.gz")
    sha256sums=('aa516016b0844e36605feb24118e686a3c3278b48b6e14caaa92a77cb477b0b4')
    _arch=amd64
else
    source=("https://s3-eu-west-1.amazonaws.com/qafoo-profiler/downloads/qprofd_i386-$pkgver.tar.gz")
    sha256sums=('486c275b233a4efd952e826ff8d17054e2d9cc0560fcae8101af52ea55f015a0')
    _arch=i368
fi

source+=('qprofd.service' 'qprofd.tmpfiles')
sha256sums+=('96043645c6f98c09df31dd5a20e68ae78afcca0b50344bc410da21a804fc69b6'
             '08b226b588223be2ccdf50954536216107a0cfb379ff0a66d74f1eba7b489cce')

package() {
    cd "${srcdir}/qprofd-${pkgver}"
    install -Dm755 qprofd "${pkgdir}"/usr/bin/qprofd
    install -Dm644 LICENSE "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE
    install -Dm644 ../qprofd.service "${pkgdir}"/usr/lib/systemd/system/qprofd.service
    install -Dm644 ../qprofd.tmpfiles "${pkgdir}"/usr/lib/tmpfiles.d/qprofd.conf
}

