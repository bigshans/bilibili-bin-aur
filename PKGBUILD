# Maintainer: msojocs <jiyecafe@gmail.com>
# Contributor: aerian<wo199710@hotmail.com>

pkgname=bilibili-bin
pkgdesc="基于 Bilibili PC 版修改的一个 Electron 打包"
_pkgname=bilibili
pkgver=1.7.2
pkgrel=1
arch=(any)
depends=('electron' libappindicator-gtk3 ffmpeg)
source=("${pkgname}-v${pkgver}-${pkgrel}.tar.gz::https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/bilibili-v${pkgver}-${pkgrel}-x86_64.tar.gz"
"${_pkgname}.desktop::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/bilibili.desktop"
"${_pkgname}.svg::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/icons/bilibili.svg"
)
sha256sums=('47addbfa12d9ad385d0ffc8a039d0fad9a817bf2f41726fd0b214db104e9a054'
            '14e4e56c5fc11c20f05545a976bc55824a623928cf5d497e2072648c98d6f16c'
            '3a7935d2d13d62fad68b4ee5aaa4832e6a202b379f2be2f80d3723f8f3993192')

package() {
    sed -i -e 's#"$root_dir/electron/electron"#electron#' $srcdir/bin/bilibili
    sed -i -e "s#Exec=bilibili#Exec=/opt/${pkgname}/bin/bilibili#" -e "s#Path=/path/to/bilibili#Path=/opt/${pkgname}/bin/#" $srcdir/$_pkgname.desktop
    install -d "$pkgdir"/opt/$pkgname
    install -d "$pkgdir"/usr/share/applications
    install -Dm644 $srcdir/$_pkgname.desktop "$pkgdir/usr/share/applications/$_pkgname.desktop"
    install -d $pkgdir/usr/share/icons/
    cp $srcdir/$_pkgname.svg $pkgdir/usr/share/icons/$_pkgname.svg
    cp -R $srcdir/{bin,app} "$pkgdir"/opt/$pkgname
}
