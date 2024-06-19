# Maintainer: msojocs <jiyecafe@gmail.com>
# Contributor: aerian<wo199710@hotmail.com>

pkgname=bilibili-bin
pkgdesc="基于 Bilibili PC 版修改的一个 Electron 打包"
_pkgname=bilibili
pkgver=1.13.6
pkgrel=2
arch=(any)
_electron=electron29
depends=("${_electron}" libappindicator-gtk3 ffmpeg)
source=("${pkgname}-v${pkgver}-${pkgrel}.tar.gz::https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/bilibili-asar-v${pkgver}-${pkgrel}.tar.gz"
"${_pkgname}.desktop::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/bilibili.desktop"
"${_pkgname}.svg::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/icons/bilibili.svg"
)
sha256sums=('d84dcec8ea3c9c3a3c768aad8c5e68f0099792d07ac17e949a6a86161b48465f'
            '2e7065c4255edcf39a9d07c83ae81e7c8a9b650c7a570c56e255e5647fd535d4'
            '7cf1a17b2a0932927396d5fd6a5c7c5b418222a405cc99322d0a730741f41b89')

package() {
    sed -i -e "s#\"\$root_dir/electron/electron\"#${_electron}#" $srcdir/bin/bilibili
    sed -i -e "s#Exec=bilibili#Exec=/opt/${pkgname}/bin/bilibili#" -e "s#Path=/path/to/bilibili#Path=/opt/${pkgname}/bin/#" $srcdir/$_pkgname.desktop
    install -d "$pkgdir"/opt/$pkgname
    install -d "$pkgdir"/usr/share/applications
    install -Dm644 $srcdir/$_pkgname.desktop "$pkgdir/usr/share/applications/$_pkgname.desktop"
    install -d $pkgdir/usr/share/icons/
    cp $srcdir/$_pkgname.svg $pkgdir/usr/share/icons/$_pkgname.svg
    cp -R $srcdir/{bin,app} "$pkgdir"/opt/$pkgname
}
