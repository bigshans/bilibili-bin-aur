# Maintainer: msojocs <jiyecafe@gmail.com>
# Contributor: aerian<wo199710@hotmail.com>

pkgname=bilibili-bin
pkgdesc="基于 Bilibili PC 版修改的一个 Electron 打包"
_pkgname=bilibili
pkgver=1.1.3
pkgrel=1
arch=(any)
depends=(electron libappindicator-gtk3 ffmpeg)
source=("${pkgname}-v${pkgver}-${pkgrel}.tar.gz::https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/bilibili-v${pkgver}-${pkgrel}-x86_64.tar.gz"
"${_pkgname}.desktop::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/bilibili.desktop"
"${_pkgname}.svg::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/icons/bilibili.svg"
)
sha256sums=('fa710438ef1793f6e7900db5dbd0c4e70f14cc4f9dd90208821438b0dfce1707'
            '50f4eea082d846e72517bf8140c5cd63dbaa24ebf4c50d663773d69669874875'
            '850a4abcf5cef98abea71ddf48b11e4147ec874e95ae51cb1fdfe38e21474ae3')

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
