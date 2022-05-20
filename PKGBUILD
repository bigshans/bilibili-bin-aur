# Maintainer: msojocs <jiyecafe@gmail.com>
# Contributor: aerian<wo199710@hotmail.com>

pkgname=bilibili-bin
pkgdesc="基于 Bilibili PC 版修改的一个 Electron 打包"
_pkgname=bilibili
pkgver=1.1.1
pkgrel=4
arch=(any)
depends=(electron)
source=("${pkgname}.tar.gz::https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/bilibili-v${pkgver}-${pkgrel}-x86_64.tar.gz"
"${_pkgname}.desktop::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/bilibili.desktop"
"${_pkgname}.svg::https://raw.githubusercontent.com/msojocs/bilibili-linux/master/res/icons/icon.svg"
)
sha256sums=('86b942b519f20b50009749d314628dd374ffa78f7d3c5cc5d07b9b652f30055c'
            '01903a46b06d73d62fd301477dfce6362effc47e3e1b2af6a1b093b19ae2af32'
            '850a4abcf5cef98abea71ddf48b11e4147ec874e95ae51cb1fdfe38e21474ae3')

package() {
    sed -i -e 's#"$root_dir/electron/electron"#electron#' $srcdir/bin/bilibili
    sed -i -e "s#Exec=bilibili#Exec=/opt/${pkgname}/bin/bilibili#" $srcdir/$_pkgname.desktop
    install -d "$pkgdir"/opt/$pkgname
    install -d "$pkgdir"/usr/share/applications
    install -Dm644 $srcdir/$_pkgname.desktop "$pkgdir/usr/share/applications/$_pkgname.desktop"
    install -d $pkgdir/usr/share/icons/
    cp $srcdir/$_pkgname.svg $pkgdir/usr/share/icons/$_pkgname.svg
    cp -R $srcdir/{bin,app} "$pkgdir"/opt/$pkgname
}
